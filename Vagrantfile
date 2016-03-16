# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.hostname = "ansible-eclipseche"
  config.ssh.forward_agent = true
  config.vm.provider "virtualbox" do |v|
    v.name = "ansible-eclipseche"
    v.memory = 4096
    v.cpus = 2
  end

  for i in 32700..32800
    config.vm.network :forwarded_port, guest: i, host: i
  end

  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "provisioning/hosts"
    ansible.playbook = "provisioning/playbook.yml"
    ansible.sudo = true
  end
end
