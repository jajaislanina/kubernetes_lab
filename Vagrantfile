# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
	if (/cygwin|mswin|mingw|bccwin|wince|emx/ =~ RUBY_PLATFORM) != nil
		config.vm.synced_folder ".", "/vagrant", mount_options: ["dmode=700,fmode=600"]
	else
		config.vm.synced_folder ".", "/vagrant"
	end

	config.vm.define "ansible" do |cfg|
		cfg.vm.box = "ubuntu/bionic64"
		cfg.vm.hostname = "ansible"
		cfg.vm.network "public_network"
		cfg.vm.provision :shell, path: "scripts/install-ansible.sh"
		cfg.vm.provider "virtualbox" do |v|
		  v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]            
		  v.memory = 2048
		end
	end
end
