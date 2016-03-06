# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |vb|
     vb.customize ["modifyvm", :id, "--memory", "2048"]
  end
 
  config.vm.define :mongo2 do |mongo2|
    mongo2.vm.hostname = "mongo2"
    mongo2.vm.network "private_network", ip: "192.168.60.11"
 
    mongo2.vm.provision :ansible do |ansible|
      ansible.playbook = "secondary.yml"
      ansible.verbose = "vv"
      ansible.sudo = true
    end
  end
 
  config.vm.define :mongo3 do |mongo3|
    mongo3.vm.hostname = "mongo3"
    mongo3.vm.network "private_network", ip: "192.168.60.12"
 
    mongo3.vm.provision :ansible do |ansible|
      ansible.playbook = "secondary.yml"
      ansible.verbose = "vv"
      ansible.sudo = true
    end
  end

  config.vm.define :mongo1 do |mongo1|
    mongo1.vm.hostname = "mongo1"
    mongo1.vm.network "private_network", ip: "192.168.60.10"
 
    mongo1.vm.provision :ansible do |ansible|
      ansible.playbook = "primary.yml"
      ansible.verbose = "vv"
      ansible.sudo = true
    end
  end

end
