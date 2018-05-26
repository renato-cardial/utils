# Vagrant Boxes
Here are vagrant boxes with specifics environments to devs

For use this boxes, you need execute the instructions below for box you need:


## PHP7 Environment
This environment have PHP 7.2, Nginx, Postgresql 9.3, Mysql 5.5, Nodejs, Docker, composer

Download box file in this url: https://drive.google.com/open?id=114e_3Ub-scR9dSuH-ktLNQnURhldhB8j

```
vagrant box add php7-environment php7-environment.box

vagrant init php7-environment

```

### Vagrantfile Sample
```
# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

Vagrant.configure("2") do |config|
  
  config.vm.box = "php7-environment"

  config.vm.network "public_network", ip: "192.168.0.10"
  #config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "~/www", "/var/www"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  
  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
     vb.memory = "1024"
  end
  
end
```