# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.disksize.size = '20GB'
  config.vm.network "forwarded_port", guest: 6006, host: 8081
  config.vm.synced_folder "../", "/code"

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    # vb.gui = true
  
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | tee /etc/apt/sources.list.d/bazel.list
    curl https://bazel.build/bazel-release.pub.gpg | apt-key add -
    apt-get update -y
    apt-get upgrade -y
    apt-get install -y lua5.1 liblua5.1-0-dev libffi-dev gettext \
                    freeglut3-dev libsdl2-dev libosmesa6-dev python-dev python-numpy \
                    python-pil realpath zip openjdk-8-jdk curl build-essential zlib1g-dev libsdl2-dev libjpeg-dev \
                    nasm tar libbz2-dev libgtk2.0-dev cmake git libfluidsynth-dev libgme-dev \
                    libopenal-dev timidity libwildmidi-dev unzip libboost-all-dev bazel
  SHELL
end
