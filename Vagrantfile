# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "UbuntuVM" do |uvm|
      uvm.vm.box = "ubuntu/trusty64"

      uvm.vm.network "private_network", ip: "192.168.1.2"
      uvm.vm.hostname = "chernenok.ubuntu"

      uvm.vm.provider :virtualbox do |vb|
          vb.name = "UbuntuVM1"
          vb.gui = true
          vb.cpus = 1
          vb.memory = "512"
      end

      uvm.vm.synced_folder "./ssh_keys", "/home/vagrant/.ssh/"

      uvm.vm.provision "shell", inline: <<-SHELL
          apt-get update
          apt-get install -y git-all
          git config --global user.name "AChernenok"
          git config --global user.email chernenokalex@gmail.com
          git clone -b module2 git@github.com:AChernenok/OSMU.git
          cat ~/OSMU/module2.txt
      SHELL
  end

  config.vm.define "CentosVM" do |cvm|
      cvm.vm.box = "centos/7"

      cvm.vm.network "private_network", ip: "192.168.1.3"
      cvm.vm.hostname = "chernenok.centos"

      cvm.vm.provider :virtualbox do |vb|
          vb.name = "CentosVM2"
          vb.gui = true
          vb.cpus = 1
          vb.memory = "512"
      end

      cvm.vm.provision "shell", inline: <<-SHELL
          yum update
      SHELL
  end
end