# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise64"

  # Credit: http://labs.qandidate.com/blog/2014/08/25/using-zfs-to-snapshot-your-database/
  $script = <<SCRIPT
sudo apt-get -y install python-software-properties
sudo apt-add-repository ppa:zfs-native/stable
sudo apt-get update
sudo apt-get -y install ubuntu-zfs
SCRIPT

  config.vm.provision "shell", inline: $script
end
