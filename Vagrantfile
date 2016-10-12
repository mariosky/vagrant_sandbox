# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  
  config.vm.define "sandbox" do |sandbox|
    sandbox.vm.box = "ubuntu/trusty64"
    

    # Create a forwarded port mapping which allows access to a specific port
    #config.vm.network "forwarded_port", guest: 6666, host: 6666

    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    sandbox.vm.network "private_network", ip: "192.168.33.10"

    sandbox.vm.provision "shell", inline: <<-SHELL
       apt-get update
       apt-get upgrade -y
    SHELL

    sandbox.vm.provision :ansible do |ansible|
      ansible.playbook = "sandbox.yml"
    end

  end

  config.vm.define "redis" do |redis|

    redis.vm.network "private_network", ip: "192.168.33.11"
    
    redis.vm.box = "ubuntu/trusty64"
    redis.vm.provision :ansible do |ansible|
      ansible.playbook = "redis.yml"
    end
  end

  

end






