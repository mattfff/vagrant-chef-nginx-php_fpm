Vagrant.configure("2") do |config|

  config.vm.box = "precise32"
  config.vm.network :forwarded_port, guest: 80, host: 8080

  #config.vm.customize do |vm|
  #  vm.memory_size = 1024
  #end

  # config.vm.network("10.234.90.20")
  # config.vm.share_folder("v-root", "/vagrant", ".", :nfs => true)
  
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.roles_path = "roles"
    chef.add_recipe("apt")
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
