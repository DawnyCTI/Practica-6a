Vagrant.configure("2") do |config|
    # Configuración para la primera máquina virtual
    config.vm.define "webserver1" do |webserver1|
      webserver1.vm.box = "ubuntu/bionic64"
      webserver1.vm.network "forwarded_port", guest: 80, host: 8081
      webserver1.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y apache2
        sudo systemctl enable apache2
        sudo systemctl start apache2
        echo "Hello from Web Server 1" | sudo tee /var/www/html/index.html
      SHELL
    end
  
    # Configuración para la segunda máquina virtual
    config.vm.define "webserver2" do |webserver2|
      webserver2.vm.box = "ubuntu/bionic64"
      webserver2.vm.network "forwarded_port", guest: 80, host: 8082
      webserver2.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y apache2
        sudo systemctl enable apache2
        sudo systemctl start apache2
        echo "Hello from Web Server 2" | sudo tee /var/www/html/index.html
      SHELL
    end
  end
  