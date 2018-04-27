Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/artful64"
  config.vbguest.auto_update = false
  config.vbguest.no_remote = true

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.name = "Ubuntu Desktop"
    vb.memory = 6144
    vb.cpus = 4

    vb.customize ["modifyvm", :id, "--vram", "256"]
    vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
    vb.customize ["modifyvm", :id, "--hwvirtex", "on"]
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
    vb.customize ["modifyvm", :id, "--graphicscontroller", "vboxvga"]
#    vb.customize 'post-boot', ["controlvm", :id, "setvideomodehint", "1920", "1080", "32"]

  end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get clean
    apt-get update
    apt-get upgrade
    sudo apt-get install virtualbox-guest-dkms -y
    apt-get install ubuntu-desktop -y
    dpkg --add-architecture i386
    add-apt-repository multiverse
    apt-get update
    apt-get dist-upgrade
    apt-get install steam -y
    reboot
  SHELL
end
