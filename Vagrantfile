Vagrant.configure("2") do |config|
  if Vagrant.has_plugin?("vagrant-vbguest")
      config.vbguest.auto_update = false  
  end
  config.vm.define :streama do |streama|
    streama.vm.box = "bento/centos-7.9"
    streama.vm.network :private_network, ip: "192.168.50.10"
    streama.vm.hostname = "streama"
    streama.vm.provision "shell", path: "./provisionStreama.sh"
  end

  config.vm.define :firewall do |firewall|
    firewall.vm.box = "bento/centos-7.9"
    firewall.vm.network :private_network, ip: "192.168.50.20"
    firewall.vm.network :public_network, ip: "192.168.1.100"
    firewall.vm.network "forwarded_port", guest: 80, host: 3000
    firewall.vm.hostname = "firewall"
    firewall.vm.provision "shell", path: "./provisionFirewall.sh"
  end
end
