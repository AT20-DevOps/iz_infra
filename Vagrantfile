Vagrant.configure("2") do |config|
  # Configure the VM 
  config.vm.box = "ubuntu/bionic64"

  # Provision
  config.vm.provision :docker
  config.vm.provision :docker_compose

  # Networking and name
  config.vm.define "ci-server" do |server|
    server.vm.network "private_network", ip: "192.168.56.60"
    server.vm.hostname = "ci-server"
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
  end

  config.vm.define "server-2" do |dockerserver|
    dockerserver.vm.provider "virtualbox" do |vb|
      vb.memory = "1504"
    end
    dockerserver.vm.network "private_network", ip: "192.168.56.61"
    dockerserver.vm.hostname = "server-2"
    dockerserver.vm.provision :shell, inline: "docker compose -f /home/vagrant/AT20_QUESTIONNAIRE_SERVICE/docker-compose.yaml up -d"
  end
end
