Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/artful64"

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.name = "Ubuntu Desktop"
    vb.memory = 4096
    vb.cpus = 2

    vb.customize ["modifyvm", :id, "--vram", "256"]
    vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
    vb.customize ["modifyvm", :id, "--hwvirtex", "on"]
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
    vb.customize ["modifyvm", :id, "--graphicscontroller", "vboxvga"]

  end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get clean
    apt-get update
    apt-get upgrade
    apt-get install lxde
    sudo dpkg --add-architecture i386
    sudo add-apt-repository multiverse
    sudo apt-get update
    sudo apt-get dist-upgrade
    sudo apt-get install steam
  SHELL
end
