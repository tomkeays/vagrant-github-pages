Vagrant.configure(2) do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.network "forwarded_port", guest: 8124, host: 8124
  config.vm.network "private_network", ip: "192.168.10.9"
  config.vm.provision "shell", inline: <<-SHELL
    echo "Updating apt-get packages and installing CURL..."
    sudo apt-get update
    sudo apt-get install -y curl
    echo "Installing RVM (Ruby Version Manager) and fetching latest build of Ruby..."
    gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
    \curl -L https://get.rvm.io | bash -s stable --ruby --autolibs=enable --auto-dotfiles
    source /home/vagrant/.rvm/scripts/rvm
    echo "Updating build-essential and git..."
    sudo apt-get install -y build-essential git
    echo "Updating existing gems..."
    sudo gem update
    sudo gem install bundle
    echo "Installing github-pages and jekyll dependencies..."
    sudo gem install github-pages
    echo "Done with provisioning."
  SHELL
  config.ssh.forward_agent = true
end
