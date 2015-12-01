# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"


  # Create a private network, which allows host-only access to the machine using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.22"
  config.vm.network "forwarded_port", guest: 3000, host: 3000, auto_correct: true 
  config.vm.network "forwarded_port", guest: 4000, host: 4000, auto_correct: true 


  # Share an additional folder to the guest VM. The first argument is the path on the host to the actual folder.
  # The second argument is the path on the guest to mount the folder.
  config.vm.synced_folder "./www", "/home/vagrant/client-app", create: true

  config.vm.synced_folder "./client", "/home/vagrant/client-app", type: "rsync", rsync__exclude: ".git/"

  # Define the bootstrap file: A (shell) script that runs after first setup of your box (= provisioning)
  config.vm.provision :shell, path: "bootstrap.sh"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1524
    v.cpus = 2
  end


end

