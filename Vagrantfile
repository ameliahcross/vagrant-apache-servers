Vagrant.configure("2") do |config|
  (1..2).each do |i|
    config.vm.define "web#{i}" do |web|
      web.vm.box = "ubuntu/bionic64"
      web.vm.hostname = "webserver#{i}"
      web.vm.network "private_network", ip: "192.168.33.10#{i}"
      web.vm.synced_folder "./www", "/var/www/html"

      web.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y apache2
        echo "<html><body><h1>Hola Mundo desde webserver#{i}</h1></body></html>" | sudo tee /var/www/html/index.html
      SHELL
    end
  end
end
