# -*- mode: ruby -*-
# vi: set ft=ruby :

## Vagrant :: Ubuntu 64 bits :: Vagrant File ##

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!

Vagrant.configure("2") do |config| 

    config.vm.box = "ubuntu/trusty64"

    # VM config
    config.vm.define :loader do |loader|
        loader.vm.network :private_network, ip: "192.168.2.1"
        loader.vm.network :forwarded_port, host: 27017, guest: 27017
        loader.vm.network :forwarded_port, host: 27018, guest: 27018
        loader.vm.network :forwarded_port, host: 3306, guest: 3306

        loader.vm.hostname = "dbloader"

        loader.vm.provider 'virtualbox' do |v|
            v.customize ['modifyvm', :id, '--name', 'ubuntu-dbloader']
            v.customize ['modifyvm', :id, '--cpus', '1']
            v.customize ['modifyvm', :id, '--memory', 1536]
            v.customize ['modifyvm', :id, '--ioapic', 'off']
            v.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
        end

        # Update package list
        loader.vm.provision :shell, :inline => 'sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927'
        loader.vm.provision :shell, :inline => 'sudo apt-get update'
    end
end
