# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    
  config.ssh.insert_key = false

  config.vm.define "master" do |master|
    master.vm.box="shekeriev/centos-8-minimal"
    master.vm.hostname = "master.dob.lab"
    master.vm.network "private_network", ip: "192.168.99.100"
    master.vm.network "forwarded_port", guest: 80, host: 8000
    master.vm.network "forwarded_port", guest: 8080, host: 8080
    master.vm.provision "shell", path: "add_hosts.sh"
  end
  
  config.vm.define "client" do |client|
    client.vm.box = "shekeriev/centos-8-minimal"
    client.vm.hostname = "client.dob.lab"
    client.vm.network "private_network", ip: "192.168.99.101"
    client.vm.provision "shell", path: "add_hosts.sh"
  end

  config.vm.define "slave" do |slave|
    slave.vm.box = "shekeriev/centos-8-minimal"
    slave.vm.hostname = "slave.dob.lab"
    slave.vm.network "private_network", ip: "192.168.99.102"
    slave.vm.network "forwarded_port", guest: 80, host: 8088
    slave.vm.provision "shell", path: "add_hosts.sh"
  end
 
end
