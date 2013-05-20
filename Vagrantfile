Vagrant.configure("2") do |config|

  config.vm.box = "precise32"
  config.vm.network :forwarded_port, guest: 80, host: 8080
  config.vm.network :private_network, ip: "192.168.1.25"

  config.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.roles_path = "roles"
    chef.add_role("drupal-fpm")

    chef.json = {
      mysql: {
        server_root_password: "root",
        server_repl_password: "root",
        server_debian_password: "root"
      }
    }
  end
end
