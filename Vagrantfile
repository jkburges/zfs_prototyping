# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise64"

  # Credit: http://labs.qandidate.com/blog/2014/08/25/using-zfs-to-snapshot-your-database/
  $script = <<SCRIPT

# Install ZFS on Ubuntu
sudo apt-get -y install python-software-properties
sudo apt-add-repository ppa:zfs-native/stable
sudo apt-get update
sudo apt-get -y install ubuntu-zfs
sudo zpool status

# Volumes, devices and pools
truncate -s 1GB /tmp/vdev1.img
truncate -s 1GB /tmp/vdev2.img
truncate -s 1GB /tmp/vdev3.img
sudo zpool create -f yolo /tmp/vdev1.img /tmp/vdev2.img /tmp/vdev3.img
sudo zpool status
sudo zfs create -o mountpoint=/mnt/zfs_playpen yolo/zfs_playpen

SCRIPT

  config.vm.provision "shell", inline: $script
end
