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
    sudo apt-mark hold grub-pc

    sudo apt-get -y -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" update
    sudo apt-get -y -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" upgrade
    sudo apt-get -y -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" install build-essential vim emacs git python openjdk-8-jdk xauth xterm
    sudo apt-get -y -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" install cgroup-bin cgroup-tools iperf libcgroup1 openvswitch-common openvswitch-switch socat
    sudo apt-get -y -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" install python-tk pyflakes pylint help2man python-setupdocs
    echo JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64 >> /etc/environment
    git clone https://github.com/mininet/mininet.git
    cd mininet
    sudo make install
  SHELL
end
