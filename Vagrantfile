Vagrant.configure(2) do |config|
  # Single Node / Master machine
  config.vm.define :master do |master|
    master.vm.box = "ubuntu/trusty64"

    master.vm.network :private_network, ip: "192.168.2.100"
    master.vm.network "forwarded_port", guest: 50070, host: 50070
    master.vm.network "public_network"
    
    master.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 1
    end

    master.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get -y upgrade
      sudo apt-get -y install language-pack-en
      sudo locale-gen en_US.UTF-8
      sudo hostname master && sudo echo "master" > /etc/hostname
    SHELL
  end
end
