# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Base Ubuntu box
  config.vm.box = "hashicorp/bionic64"

  # Private network IP
  config.vm.network "private_network", ip: "192.168.33.10"

  # Provisioning script
  config.vm.provision "shell", inline: <<-SHELL
    # Update package list
    sudo apt-get update -y

    # Install Apache and Git
    sudo apt-get install -y apache2 git

    # Replace default index.html content
    echo "Hello from the updated Vagrant setup" | sudo tee /var/www/html/index.html

    # Ensure Apache starts on boot
    sudo systemctl enable apache2
    sudo systemctl restart apache2
  SHELL
end
