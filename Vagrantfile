# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  (1..1).each do |i|
    config.vm.define "nginx#{i}" do |o|
      o.vm.box = "centos/7"
      o.vm.hostname = "nginx#{i}"
      o.vm.network "private_network", ip: "172.16.18.#{i}", netmask: "255.240.0.0"
      o.vm.provision :shell, inline: "sed 's/127\.0\.0\.1.*nginx.*/172\.16\.18\.#{i} nginx#{i}/' -i /etc/hosts"
      o.vm.provider "virtualbox" do |v|
        v.name = "nginx#{i}"
        v.memory = 1024
        v.gui = false
      end
    end
  end
end
