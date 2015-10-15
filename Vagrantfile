# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  
  config.vm.define 'dataduct' do |dataduct|
    dataduct.vm.box = 'ubuntu/trusty64'
    dataduct.vm.host_name = 'dataduct'
    dataduct.vm.network 'private_network', ip: '192.168.1.3'

    dataduct.vm.provision "ansible" do |ansible|
      ansible.limit = 'dataduct'
      ansible.inventory_path = 'provisioning/hosts'
      ansible.playbook = 'provisioning/playbook.yaml'
    end

    # For some reason Python Pandas needs at least 2gb of memory to install
    dataduct.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
    end
  end
end
