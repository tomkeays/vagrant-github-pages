Vagrant.configure(2) do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.network "forwarded_port", guest: 8124, host: 8124
  config.vm.network "private_network", ip: "192.168.10.9"
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get -y install build-essential git ruby1.9.3
    sudo gem install github-pages --no-ri --no-rdoc
  SHELL
  config.ssh.forward_agent = true
end
