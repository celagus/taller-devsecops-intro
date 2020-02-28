# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "celagus/test-devsecops"
  config.vm.box_version = "0.1.0"
  
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 80, host: 8008

  config.vm.network "private_network", ip: "10.20.30.40", mask:"255.255.255.0"
  config.vm.boot_timeout = 600
  config.vm.hostname = "jenkins-taller-dso.localhost"
  config.vm.provider "virtualbox" do |v|
	v.name = "jenkins-taller-dso"
  end

  config.vm.synced_folder ".", "/vagrant"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
end
