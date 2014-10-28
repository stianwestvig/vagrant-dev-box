# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/precise64"
  config.vm.network :private_network, ip: '192.168.50.50'
  config.vm.synced_folder "salt/roots/", "/srv/", :nfs => { :mount_options => ["dmode=777","fmode=777"] }
  config.vm.network :forwarded_port, host: 1337, guest: 1337
  config.vm.network :forwarded_port, host: 1336, guest: 1336
  config.vm.provision :salt do |salt|
    salt.minion_config = "salt/minion"
    salt.run_highstate = true
    salt.verbose = true
  end
end