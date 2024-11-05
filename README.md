Verificar en el servidor maestro y esclavo el mysql client, si no instalar; 

sudo apt-get install mysql-server

CONFIGURACIÓN DEL MAESTRO: 

Abrir /etc/mysql/my.cnf y comentar la línea #bind_address
Luego agregar justo abajo de la casilla [mysqld]

server-id = 1
log_bin = /var/log/mysql/mysql-bin.log
binlog-ignore-db = "mysql"

Restablecer el servicio de mysql.

Ahora se crea el user para la replicación de maestr-esclavo

mysql -u root -p
create user 'replica'@'192.168.56.103' identified by 'replica';
grant replication slave on *.* to 'replica'@'192.168.56.103' identified by 'replica;
flush privileges;

flush table with read lock;
show master status;

El estado del maestro debe reflejar un File y una position, tener en cuenta ya que los
usaremos en los esclavos.

CONFIGURACIÓN DE ESCLAVOS:

tambien comentar #bind_address

server-id = 2 # cambia el id a 3 para el esclavo siguente
relay-log = /var/log/mysql/mysql-relay-bin.log
bin_log = /var/log/mysql/mysql-bin.log
binlog-ignored-db = "mysql"

restablecer ambos

change master to master_host='192.168.56.102', master_user='replica',
master_password='replica', 
master_log_file='mysql-bin.000001', master_log_pos=624;

iniciar el esclavo 

start slave;

show slave status \G y verificar que 
slave_IO_Running y SQL_Running están en yes 
significa que la replicación y configurarición es exitosa

Por último se hace las pruebas para verificar conectividad.

HAPROXY;
En los servidores maestro y esclavo se ingresa el usuario en este caso el haproxy_user; 

mysql -u root -p
USE mysql;
INSERT INTO user (HOST, USER) VALUES('192.168.56.101', 'haproxy_user');
flush privileges;

También darle permisos para que permita ejecutar las pruebas 

GRANT ALL PRIVILEGES ON *.* TO 'haproxy_root'@'192.168.56.101'
IDENTIFIED BY 'haproxy_root_pass' WITH GRANT OPTION;
flush privileges;

Siguente instalar mysql, y haproxy 

sudo apt-get install mysql-client;

sudo apt-get install haproxy;

realizar una copia sudo cp /etc/haproxy/haproxy.cfg{,.original}
Configurar el balanceo, seria algo similar a esto: 

global
    log 127.0.0.1 local0
    chroot /var/lib/haproxy
    maxconn 100
    user haproxy
    group haproxy

defaults
    log global
    option tcplog
    retries 2
    timeout client 30m
    timeout connect 4s
    timeout server 30m
    timeout check 5s

listen stats
    mode http
    bind *:9201
    stats enable
    stats uri /stats
    stats realm Strictly\ Private
    stats auth kanyi:test

listen mysql-cluster
    bind :3306
    mode tcp
    option mysql-check user haproxy_user
    balance roundrobin
    server master 192.168.56.102:3306 check
    server slave1 192.168.56.103:3306 check
    server slave2 192.168.56.104:3306 check

Por último : sudo service haproxy restart; 

Ya deberia funcionar el balanceo exitosamente.

Se puede hacer pruebas para comprobar 
mysql -h 127.0.0.1 -u haproxy_root -p -e "show variables like 'server_id'";
