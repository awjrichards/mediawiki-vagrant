# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|

	config.vm.box = "precise32"
	config.vm.box_url = "http://files.vagrantup.com/precise32.box"

	# Boot with a GUI so you can see the screen. (Default is headless)
	# config.vm.boot_mode = :gui

	# Assign this VM to a bridged network, allowing you to connect directly to a
	# network using the host's network device. This makes the VM appear as another
	# physical device on your network.
	config.vm.network :bridged

	# Forward tcp://host:8080 => tcp://guest:80
	config.vm.forward_port 80, 8080

	# Mount "./mediawiki" as "/srv/mediawiki" in the guest VM.
	config.vm.share_folder "mediawiki", "/srv/mediawiki", "mediawiki"

	Vagrant::Config.run do |config|

		config.vm.provision :puppet do |puppet|
			puppet.options = "--verbose --debug"
			puppet.module_path = "modules"
			puppet.manifests_path = "manifests"
			puppet.manifest_file = "base.pp"
		end
	end

end