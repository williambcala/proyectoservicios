<<<<<<< HEAD
Vagrant.configure("2") do |config|
  config.vm.define "haproxy" do |haproxy|
    haproxy.vm.box = "ubuntu/trusty64"
    haproxy.vm.hostname = "haproxy"
    
    haproxy.vm.network :private_network, ip: "192.168.56.101"
    haproxy.vm.network :forwarded_port, guest: 22, host: 10122, id: "ssh"

    haproxy.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "haproxy-x"]
    end
  end

  config.vm.define "db1" do |db1|
    db1.vm.box = "ubuntu/trusty64"
    db1.vm.hostname = "db1"
    
    db1.vm.network :private_network, ip: "192.168.56.102"
    db1.vm.network :forwarded_port, guest: 22, host: 10222, id: "ssh"

    db1.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "db1-x"]
    end
  end

  config.vm.define "db2" do |db2|
    db2.vm.box = "ubuntu/trusty64"
    db2.vm.hostname = "db2"
    
    db2.vm.network :private_network, ip: "192.168.56.103"
    db2.vm.network :forwarded_port, guest: 22, host: 10322, id: "ssh"

    db2.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "db2-x"]
    end
  end

  config.vm.define "db3" do |db3|
    db3.vm.box = "ubuntu/trusty64"
    db3.vm.hostname = "db3"
    
    db3.vm.network :private_network, ip: "192.168.56.104"
    db3.vm.network :forwarded_port, guest: 22, host: 10422, id: "ssh"

    db3.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "db3-x"]
    end
  end
end

=======
Vagrant.configure("2") do |config|
  config.vm.define "haproxy" do |haproxy|
    haproxy.vm.box = "ubuntu/trusty64"
    haproxy.vm.hostname = "haproxy"
    
    haproxy.vm.network :private_network, ip: "192.168.56.101"
    haproxy.vm.network :forwarded_port, guest: 22, host: 10122, id: "ssh"

    haproxy.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "haproxy-x"]
    end
  end

  config.vm.define "db1" do |db1|
    db1.vm.box = "ubuntu/trusty64"
    db1.vm.hostname = "db1"
    
    db1.vm.network :private_network, ip: "192.168.56.102"
    db1.vm.network :forwarded_port, guest: 22, host: 10222, id: "ssh"

    db1.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "db1-x"]
    end
  end

  config.vm.define "db2" do |db2|
    db2.vm.box = "ubuntu/trusty64"
    db2.vm.hostname = "db2"
    
    db2.vm.network :private_network, ip: "192.168.56.103"
    db2.vm.network :forwarded_port, guest: 22, host: 10322, id: "ssh"

    db2.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "db2-x"]
    end
  end

  config.vm.define "db3" do |db3|
    db3.vm.box = "ubuntu/trusty64"
    db3.vm.hostname = "db3"
    
    db3.vm.network :private_network, ip: "192.168.56.104"
    db3.vm.network :forwarded_port, guest: 22, host: 10422, id: "ssh"

    db3.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "db3-x"]
    end
  end
end
>>>>>>> 46fbddf (Añadiendo el proyecto proxy)
