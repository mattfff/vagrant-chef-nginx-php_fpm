Vagrant::Config.run do |config|

  config.vm.box = "precise32"

  config.vm.customize do |vm|
    vm.memory_size = 1024
  end

  # config.vm.network("10.234.90.20")
  # config.vm.share_folder("v-root", "/vagrant", ".", :nfs => true)
  
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.add_role("drupal-fpm")
  end
end
