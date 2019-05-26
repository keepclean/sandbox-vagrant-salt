# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"
  config.vm.hostname = "deb01"
  config.vm.network "private_network", ip: "192.168.56.4", :name => 'vboxnet0', :adapter => 2

  config.vm.provider "virtualbox" do |vb|
    vb.name = "deb01"
    vb.memory = "1024"
    vb.default_nic_type = "virtio"
  end

  config.vm.synced_folder "~/Code/infra/salt", "/srv/salt/", type: "nfs"

  config.vm.provision :salt do |salt|
    salt.masterless = true
    salt.minion_config = "~/Code/infra/salt/configs/minion"
    salt.minion_id = "deb01"
    salt.run_highstate = true

    salt.python_version = "3"
  end

end
