
Vagrant.configure(2) do |config|

  # Specify the base box
  config.vm.box = "ubuntu/trusty64"

  # Setup port forwarding
  config.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
  config.vm.network "forwarded_port", host_ip: "127.0.0.1", guest: 3306, host: 3309, auto_correct: true

  # Setup network
  config.vm.network "private_network", ip: "192.168.33.10"

  # Setup synced folder
  config.vm.synced_folder "shared/", "/var/www", group: "www-data", owner: "vagrant", :mount_options => ['dmode=775', 'fmode=775']

  # CUSTOMIZATION
  config.vm.provider "virtualbox" do |vb|

     vb.name = "seedBox"
  
     # Customize the amount of memory on the VM:
     vb.memory = "1024"
     vb.cpus = 1
   end


  # PROVISION
  config.vm.provision "shell" do |s|
      s.path = "vagrant/bootstrap.sh"
  end
  
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  #   sudo apt-get install -y apache2
  # SHELL
end
