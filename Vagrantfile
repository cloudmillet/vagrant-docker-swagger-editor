# -*- mode: ruby -*-
# vi: set ft=ruby :


# update OS and install docker 
$commonscript = <<-SCRIPT
sudo yum update -y
sudo echo "LANG=en_US.utf-8" > /etc/environment
sudo echo "LC_ALL=en_US.utf-8" >> /etc/environment
sudo curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker vagrant
sudo systemctl enable docker
sudo systemctl start docker
sudo docker version
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo yum install git -y
sudo yum install jq -y
sudo yum install net-tools -y
mkdir Swagger 
cd swagger
docker pull swaggerapi/swagger-editor
docker run -d -p 8080:8080 swaggerapi/swagger-editor
SCRIPT

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
    config.vm.define "docker_lab" do |docker_lab|
      # Every Vagrant development environment requires a box. You can search for
      # boxes at https://vagrantcloud.com/search.         
         docker_lab.vm.box = "centos/7"
         docker_lab.vm.network "forwarded_port", guest: 8080, host: 8080
         
      # Memory and CPU allocation
         docker_lab.vm.provider "virtualbox" do |v|
            v.memory = 2048
            v.cpus = 2
         end
         # Create a forwarded port mapping which allows access to a specific port
         # within the machine from a port on the host machine and only allow access
         # via 127.0.0.1 to disable public access
        
         # Host name allocation
         docker_lab.vm.hostname = "dockerlab.example.com"

         # Installing required packages for docker  node
        docker_lab.vm.provision "shell", inline: $commonscript
       
         
         # Share an additional folder to guest VM.  The first argument is the path on the hst to the actual folder. 
         # The Second argument is the path on the guest to mount the floder
        
   end
end
