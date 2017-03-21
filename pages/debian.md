---
layout: page
subtitle: "Debian 8.7 networking"
description: "configure /etc/network/interfaces file"
permalink: /pages/debian_networking
---
### Debian 8.7 VM

* First, debian has not `sudo` command, so let install:

      su
      apt-get install sudo
      adduser username sudo

* Second, we add our username on the file `/etc/sudoers`:
    
      su
      nano /etc/sudoers

* Third, add the following line:

      usernamehere  ALL=(ALL:ALL) ALL

* Four, installing components:

      sudo apt-get update
      sudo apt-get install lsb-core htop
      sudo cp /sbin/ifconfig /usr/local/bin/

* Configure the network interfaces:

      sudo nano /etc/network/interfaces

* Add or modify:

      auto eth0
      iface eth0 inet static
      address 192.168.100.133
      netmask 255.255.255.0
      network 192.168.100.0
      gateway 192.168.100.1
      broadcast 192.168.100.255
      dns-nameservers 8.8.8.8 8.8.4.4

* Restart the services:

      sudo /etc/init.d/networking restart
    
* Now, we connect from the OS host through ssh:

      ssh jenazad@192.168.100.133

