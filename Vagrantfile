Vagrant.configure(2) do |config|
  config.vm.box = "opscode_ubuntu-14.04_chef-provisionerless"
  config.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_ubuntu-14.04_chef-provisionerless.box"

  config.vm.network "private_network", ip: "192.168.33.30"
  config.vm.synced_folder "../dev", "/home/vagrant/dev", create: true, owner: "vagrant", group: "vagrant"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.provision "chef_zero" do |chef|
    chef.version = '11.18.0'
    chef.cookbooks_path = "./cookbooks"
    chef.add_recipe "apt"
    chef.add_recipe "ruby_build"
    chef.add_recipe "rails_support"
    chef.add_recipe "rbenv::user"
    chef.json = {
      "rbenv" => {
        "user_installs" => [{
          "user" => "vagrant",
          "rubies" => ["2.1.5"],
          "global" => "2.1.5",
          "gems" => { "2.1.5" => [{"name" => "bundler"}] }
        }]
      }
    }
  end
end
