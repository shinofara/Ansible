# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define :node1 do |node|
    node.vm.box = "centos64"
    node.vm.network :public_network
    node.vm.network :private_network, ip: "192.168.33.11"
  end
  
  config.vm.define :node2 do |node|
    node.vm.box = "centos64"
    node.vm.network :public_network
    node.vm.network :private_network, ip: "192.168.33.12"
  end

  config.vm.define :node3 do |node|
    node.vm.box = "centos64"
    node.vm.network :public_network
    node.vm.network :private_network, ip: "192.168.33.13"

    node.vm.provision "ansible" do |ansible|
        ansible.groups = {
            "servers" => ["node3"]
        }

        ansible.playbook = "provisioning/ruby.yml"
    end
  end

end
