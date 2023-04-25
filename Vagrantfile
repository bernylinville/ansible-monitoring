# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "bernylinville/centos7"
  config.ssh.insert_key = false
  config.vm.provider "libvirt"

  config.vm.provider :libvirt do |l|
    l.memory = 8192
    l.cpus = 4
  end

  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "test/inventories/monitoring/inventory"
    ansible.galaxy_role_file = "requirements.yml"
    ansible.playbook = "monitoring.yml"
    ansible.become = true
    ansible.limit = "all"
  end
end