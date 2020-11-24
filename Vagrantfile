# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"
  # Setup private network
  config.vm.network "private_network" , ip: "192.168.10.10"
  # Create a host to point to our internal IP
  config.vm.hostname = "www.sam-dev-env-provisional.local"

end
