# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.network "private_network", type: "dhcp"
  config.vm.define "ubuntu1604", primary: true do |node|
    node.vm.box = "geerlingguy/ubuntu1604"
    node.vm.provision "ansible" do |ansible|
      ansible.verbose = "vvv"
      ansible.playbook = "setup.yml"
      ansible.sudo = true
    end
  end
end
