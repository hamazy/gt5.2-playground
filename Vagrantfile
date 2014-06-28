# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.network "public_network"

  config.vm.provision "ansible" do |ansible|
    ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
    ansible.groups = {
      "sensei" => ["sensei"],
      "all_groups:children" => ["sensei"]
    }
    ansible.playbook = "provisioning/playbook.yml"
  end

  config.vm.define "sensei" do |sensei|
    sensei.vm.box = "ubuntu/trusty64"
    sensei.vm.hostname = "sensei.local"
  end

end
