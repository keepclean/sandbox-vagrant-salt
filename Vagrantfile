# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"
  config.vm.hostname = "deb01"
  config.vm.network "private_network", ip: "10.0.0.44", :adapter => 2

  config.vm.provider "virtualbox" do |vb|
    vb.name = "deb01"
    vb.memory = "1024"
    vb.default_nic_type = "virtio"
  end

  config.vm.synced_folder "salt/", "/srv/salt/", type: "nfs"

  config.vm.provision :salt do |salt|
    salt.masterless = true
    salt.install_master = false
    salt.run_highstate = true
    salt.run_overstate = false
    salt.orchestrations = false
    salt.minion_config = "configs/minion"
    salt.minion_id = "deb01"
    salt.bootstrap_options = "-d -X -x python3"
    salt.python_version = "3"
  end

end
