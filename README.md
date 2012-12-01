AmberBox
========

AmberBox is a ready-to-start-developing-in-rails Vagrant box.

What is included?

1. RVM & rubies: 1.9.3, 1.9.2, 1.8.7
2. Databases: MySQL, PostgreSQL, mongodb, redis-server
3. ZSH + Oh-my-zsh config
4. tmux, screen
5. Vim + Janus
6. Firefox 14, Xvfb - for running your Selenium tests

Some default configuration:
- forwards localhost:3000 to port 3000 at virtual machine
- sets networking in 192.168.33.0 network (VM is 192.168.33.3)
- enables X11 forwarding (if you want to run selenium from within VM)
- cool AmberBit motd

Steps to get it up and running:

1. Install VirtualBox 4.2 from here: https://www.virtualbox.org/wiki/Downloads
2. Install Vagrant from here:
http://downloads.vagrantup.com/tags/v1.0.5  or as a ruby gem: gem
install vagrant
3. Add amberbox Vagrant box to your local library of boxes

    $ vagrant box add amberbox https://github.com/downloads/amberbit/amberbox/amberbox.box    

This requires downloading 829 MB box file. After this step, you should   
have 'amberbox' box installed in your system, and you can init
your development boxes from it.

4. Create virtual machine for your project

Run:

     $ mkdir my_project_name && cd my_project_name
     $ vagrant init amberbox
     $ vagrant up
     $ vagrant ssh

Modifying Vagrantfile:

The box has defaults that might not suit you. For example, it gives by
default up to 2GB of your RAM for the VM. Settings I customized, that
you most likely want to tweak in Vagrantfile are

    config.vm.customize ["modifyvm", :id, "--memory", 2048]
    config.vm.network :hostonly, "192.168.33.3"
    config.ssh.forward_x11 = true
    config.vm.forward_port 3000, 3000
    
    
Credits
=======

Brought to you by AmberBit Ruby on Rails development team (http://www.amberbit.com).

Based on Vagrant box: https://dl.dropbox.com/u/1543052/Boxes/UbuntuServer12.04amd64.box
Get more boxes from: http://vagrantbox.es
