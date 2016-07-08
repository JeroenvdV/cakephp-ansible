# -*- mode: ruby -*-
# vi: set ft=ruby :
s = File.foreach('defaults/user.yml').grep /http_domain/
httpdomain = s.to_s.split(': ')[-1].split('\\')[0]

required_plugins = %w(vagrant-hostsupdater)

plugins_to_install = required_plugins.select { |plugin| not Vagrant.has_plugin? plugin }
if not plugins_to_install.empty?
  puts "Installing plugins: #{plugins_to_install.join(' ')}"
  if system "vagrant plugin install #{plugins_to_install.join(' ')}"
    exec "vagrant #{ARGV.join(' ')}"
  else
    abort "Installation of one or more plugins has failed. Aborting."
  end
end

Vagrant.configure("2") do |config|

  config.vm.network "private_network", ip: "172.28.128.5"
  config.vm.hostname = httpdomain
  config.vm.define "ubuntu1604", primary: true do |node|
    node.vm.box = "geerlingguy/ubuntu1604"
    node.vm.provision "ansible" do |ansible|
      ansible.verbose = "vvv"
      ansible.playbook = "setup.yml"
      ansible.sudo = true
    end
  end
end
