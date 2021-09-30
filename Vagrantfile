# -*- mode: ruby -*-
# vi: set ft=ruby :

# Lab 4
# v1.0.0

# Vagrant do loop start

Vagrant.configure("2") do |config|

# use the Ubuntu vagrant template (aka "box")

 config.vm.box = "ubuntu/bionic64"

# port forward for the web server, we'll keep everything
# behind the nat network.

 config.vm.network "forwarded_port", guest: 80, host: 80


 config.vm.provider "virtualbox" do |vb|
  # Display the VirtualBox GUI when booting the machine
  vb.gui = true

  # Customize the amount of memory on the VM:
  vb.memory = "2048"

  # Customize CPU cores - student adds code here
  vb.cpus = 2
 end

# Use the Vagrant Provisioner to install some of the packages
# needed for LAMP stack.
#

 config.vm.provision "shell", inline: <<-SHELL
 apt update
 apt install -y apache2

 sudo apt install -y mariadb-server
 sudo apt install -y php
 sudo apt install -y libapache2-mod-php
 sudo apt install -y php-mysql

 SHELL

# For practice, let's have Vagrant copy a file out to the server.
# This file won't do anything, but is just an example of how we could
# Transfer a file of database users for example.  That some future
# automation would use add users to the database.  
# On your windows or mac, create an empty text file named "users.sql"
# put it in the same directory as your Vagrant VM directory
# Then have Vagrant copy it out to the server.
# Research how to do this on the web.
# For the love of god don't just search the entire freakin' web...
# don't use some guide from 
# http://imsomemediocredeveloperwhothinksheknowseverythingbutreallydoesnt.com
#
# Go straight to here: https://www.vagrantup.com/docs/provisioning/file

# put your killer command for copying a file to the VM here.
# Remember that at this time the copying of this file serves no useful
# purposeful. It will soon.  Vagrant will copy the file into the
# /home/vagrant directory.
# Hint: your statement to copy users.sql should start like this:

# config.vm.provision "file" #more stuff goes here.
 config.vm.provision "file", source: "/Users/thomasoselio/Documents/INET4031/users.sql", destination: "/home/vagrant"

end