# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  # Define a vagrant machine for the CONTINUOUS INTEGRATION server
  # --------------------------------------------------------------
  config.vm.define "ci" do |ci|
      # Create a private network, which allows host-only access to the machine
	  # using a specific IP.
	  ci.vm.network "private_network", ip: "192.168.33.10"

	  ci.vm.hostname = "ci"

	  # Provider-specific configuration so you can fine-tune various
	  # backing providers for Vagrant. These expose provider-specific options.
	  # Example for VirtualBox:
	  #
	  ci.vm.provider "virtualbox" do |vb|
		# Display the VirtualBox GUI when booting the machine
		vb.gui = false
		# Customize the amount of memory on the VM:
		vb.memory = "2048"
	  end

	  # Enable provisioning with a shell script. Additional provisioners such as
	  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
	  # documentation for more information about their specific syntax and use.
	  # config.vm.provision "shell", inline: <<-SHELL
	  #   sudo apt-get update
	  #   sudo apt-get install -y apache2
	  # SHELL  
	 # ci.vm.provision :shell, path: "bootstrap_ci.sh"
		require 'rbconfig'
		is_windows = (RbConfig::CONFIG['host_os'] =~ /mswin|mingw|cygwin/)
		if is_windows
			# Provisioning configuration for shell script.
			ci.vm.provision "shell" do |sh|			
				sh.path = "playbooks/JJG-Ansible-Windows/windows.sh"
				sh.args = "playbooks/ci.yml"				
			end
		else
			ci.vm.provision "ansible" do |ansible|
				ansible.playbook = "playbooks/ci.yml"
			end
		end
  end


  # Define a vagrant machine for the TEST server
  # --------------------------------------------
  config.vm.define "test" do |test|
      # Create a private network, which allows host-only access to the machine
	  # using a specific IP.
	  test.vm.network "private_network", ip: "192.168.33.20"

	  test.vm.hostname = "test"

	  # Provider-specific configuration so you can fine-tune various
	  # backing providers for Vagrant. These expose provider-specific options.
	  # Example for VirtualBox:
	  #
	  test.vm.provider "virtualbox" do |vb|
		# Display the VirtualBox GUI when booting the machine
		vb.gui = false
		# Customize the amount of memory on the VM:
		vb.memory = "512"
	  end

	  # Enable provisioning with a shell script. Additional provisioners such as
	  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
	  # documentation for more information about their specific syntax and use.
	  # config.vm.provision "shell", inline: <<-SHELL
	  #   sudo apt-get update
	  #   sudo apt-get install -y apache2
	  # SHELL  
		require 'rbconfig'
		is_windows = (RbConfig::CONFIG['host_os'] =~ /mswin|mingw|cygwin/)
		if is_windows
			# Provisioning configuration for shell script.
			test.vm.provision "shell" do |sh|
				sh.path = "playbooks/JJG-Ansible-Windows/windows.sh"
				sh.args = "playbooks/test.yml"
			end
		else
			test.vm.provision "ansible" do |ansible|
				ansible.playbook = "playbooks/test.yml"
			end
		end
  end
  
  
  # Define a vagrant machine for the PROD server
  # --------------------------------------------
  config.vm.define "prod" do |prod|
      # Create a private network, which allows host-only access to the machine
	  # using a specific IP.
	  prod.vm.network "private_network", ip: "192.168.33.30"

	  prod.vm.hostname = "prod"

	  # Provider-specific configuration so you can fine-tune various
	  # backing providers for Vagrant. These expose provider-specific options.
	  # Example for VirtualBox:
	  #
	  prod.vm.provider "virtualbox" do |vb|
		# Display the VirtualBox GUI when booting the machine
		vb.gui = false
		# Customize the amount of memory on the VM:
		vb.memory = "512"
	  end

	  # Enable provisioning with a shell script. Additional provisioners such as
	  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
	  # documentation for more information about their specific syntax and use.
	  # config.vm.provision "shell", inline: <<-SHELL
	  #   sudo apt-get update
	  #   sudo apt-get install -y apache2
	  # SHELL  
		require 'rbconfig'
		is_windows = (RbConfig::CONFIG['host_os'] =~ /mswin|mingw|cygwin/)
		if is_windows
			# Provisioning configuration for shell script.
			prod.vm.provision "shell" do |sh|
				sh.path = "playbooks/JJG-Ansible-Windows/windows.sh"
				sh.args = "playbooks/prod.yml"
			end
		else
			prod.vm.provision "ansible" do |ansible|
				ansible.playbook = "playbooks/prod.yml"
			end
		end
  end
end
