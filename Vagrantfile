$script = <<-SCRIPT
echo "I like Vagrant"
echo "I love Linux"
touch file3
SCRIPT

Vagrant.configure("2") do |config|
  #configurate the VM 
  config.vm.box = "ubuntu/bionic64"
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
  #provision
  config.vm.provision:docker
  config.vm.provision:shell, path:"bootstrap.sh"
  config.vm.provision:file, source: "newfile" , destination: "newfile"
  config.vm.provision:file, source: "HTML", destination: "HTMLDIR"

#networking and name
  config.vm.define "server-1" do |dockerserver|
    dockerserver.vm.network "private_network", ip:'192.168.56.60'
    dockerserver.vm.hostname = "dockerserver"
    dockerserver.vm.provision :shell, inline:  "echo Hi class from vagrant"
    dockerserver.vm.provision :shell, inline:  $script
    dockerserver.vm.provision :shell do |s|
      s.inline = "echo $1"
      s.args = ["AT","Class!"]
    end      
    dockerserver.vm.provision "docker" do |d|
      d.run "hello-world"
    end
  end
end
