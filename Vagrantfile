# -*- mode: ruby -*-
# vi: set ft=ruby :

# you will need to have the environment variable ALE_ROOT set in order
# to proceed here.  ALE_ROOT has to point to the root of the cloned 
# Arcade Learning Environment ( https://github.com/mgbellemare/Arcade-Learning-Environment )
ale_root  = ENV['ALE_ROOT']
base_path = "/home/vagrant/arcade_env" 
unless ale_root.nil?
 Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.89"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder ale_root, base_path 

  # VirtualBox settings:
  #
  config.vm.provider :virtualbox do |vb|
    vb.customize ['modifyvm', :id, '--memory', '2048']
    vb.customize ['modifyvm', :id, '--cpus', '2']
  end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
     cd "#{base_path}"
     sudo apt-get update
     sudo apt-get install -y build-essential
     # python dependencies
     sudo apt-get -y install python-pip python-numpy
     sudo pip install numpy
     # pick the correct makefile...
     cp "#{base_path}/makefile.unix" makefile
     # ALE dependencies
     sudo apt-get -y install libsdl1.2-dev libsdl-gfx1.2-dev libsdl-image1.2-dev cmake 
     cmake -DUSE_SDL=ON -DUSE_RLGLUE=OFF -DBUILD_EXAMPLES=ON .
     make -j 4
     # install the ale_interface just built
     sudo pip install .
  SHELL
 end
end
