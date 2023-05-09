
Vagrant.configure("2") do |config|
  #configurate the VM 
  config.vm.box = "ubuntu/bionic64"
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
  #provision
    config.vm.provision:docker
  #networking and name
    config.vm.define "server-1" do |dockerserver|
      dockerserver.vm.network "private_network", ip:'192.168.56.60'
      dockerserver.vm.hostname = "dockerserver"
    end
end
