# -*- mode: ruby -*-
# vi: set ft=ruby :


#Bootstrap script for installing Go and setting correct environments
$bootstrapScript = <<SCRIPT
GO_VERSION=1.3.3

echo 'Updating and installing ubuntu packages...'
sudo apt-get update

echo 'Downloading go$GO_VERSION.linux-amd64.tar.gz'
wget –quiet https://storage.googleapis.com/golang/go$GO_VERSION.linux-amd64.tar.gz

echo 'Unpacking go language'
sudo tar -C /usr/local -xzf go$GO_VERSION.linux-amd64.tar.gz

echo 'Setting upp correct env. variables'
echo "export GOPATH=/vagrant/" >> /home/vagrant/.bashrc
echo "export PATH=$PATH:$GOPATH/bin:/usr/local/go/bin" >> /home/vagrant/.bashrc
SCRIPT

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Using Ubuntu 14.04
  config.vm.box = "ubuntu/trusty64"
  # Forwarding port 8080 to local 8080.
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  #Calling bootstrap setup
  config.vm.provision "shell", privileged: false, inline: $bootstrapScript
end
