# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.network "forwarded_port", guest: 8181, host: 8181

  config.vm.provider "virtualbox" do |vb|
    vb.name = "mininet-tcn6430"
    # Display the VirtualBox GUI when booting the machine
    # vb.gui = true
  
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    export DEBIAN_FRONTEND=noninteractive
    export OPTS=-y -o Dpkg::Options::="--force-confnew"

    sudo apt-get $OPTS update
    sudo apt-get $OPTS upgrade
    sudo apt-get $OPTS install build-essential vim emacs git python mininet openjdk-8-jdk
    echo JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64 >> /etc/environment
  SHELL
end
