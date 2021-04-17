Vagrant.configure("2") do |config|
  config.vm.define "UbuntuVM1" do |uvm|
      uvm.vm.box = "ubuntu/trusty64"

      uvm.vm.network "private_network", ip: "192.168.10.2"
      uvm.vm.hostname = "chernenok.ubuntu1"

      uvm.vm.provider :virtualbox do |vb|
          vb.name = "chernenokUbuntu1"
          vb.gui = true
          vb.cpus = 1
          vb.memory = "512"
      end

      uvm.vm.synced_folder "./ssh_keys", "/home/vagrant/.ssh/"

      uvm.vm.provision "shell", inline: <<-SHELL
          sudo apt-get update
          apt-get install -y git-all
          sudo apt-get install docker-engine -y
          sudo service docker start
          sudo docker run hello-world
          ALL=(ALL) NOPASSWD:ALL >> /etc/sudoers
          usermod -aG wheel vagrant
      SHELL
  end

  config.vm.define "UbuntuVM2" do |uvm|
      uvm.vm.box = "ubuntu/trusty64"

      uvm.vm.network "private_network", ip: "192.168.10.3"
      uvm.vm.hostname = "chernenok.ubuntu2"

      uvm.vm.provider :virtualbox do |vb|
          vb.name = "chernenokUbuntu2"
          vb.gui = true
          vb.cpus = 1
          vb.memory = "512"
      end

      cvm.vm.provision "shell", inline: <<-SHELL
          sudo apt-get update
      SHELL
  end
end
