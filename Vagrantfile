# -*- mode: ruby -*-
# vi: set ft=ruby et ts=2 sw=2:

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "chef/debian-6.0.8"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "test.yml"
    ansible.inventory_path = "inventory/vagrant.ini"
    #ansible.verbose = "vvvv"
  end

  config.vm.define "mysql" do |mysql|
    mysql.vm.network "private_network", ip: "192.168.42.21"
    mysql.vm.hostname = "mysql.pascutti.local"
  end

  config.vm.define "php" do |php|
    php.vm.network "private_network", ip: "192.168.42.31"
    php.vm.hostname = "php-01.pascutti.local"

    php.vm.synced_folder "web", "/var/www/default"
  end
end
