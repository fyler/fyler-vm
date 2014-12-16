Vagrant.configure("2") do |config|

  config.vm.box       = "ubuntu/trusty64"
  config.vm.box_url   = "https://atlas.hashicorp.com/ubuntu/boxes/trusty64/versions/14.04/providers/virtualbox.box"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "priv/ansible/fyler_dev.yml"
    ansible.inventory_path = "priv/ansible/dev_hosts"
    ansible.tags = ENV["TAGS"]
    ansible.skip_tags = ENV["SKIP_TAGS"]
    ansible.verbose = 'v'
    ansible.limit = "all" 
  end

  config.vm.network :forwarded_port, host: 2203, guest: 22 
  config.vm.network "forwarded_port", guest: 8008, host: 8008

  config.vm.network "private_network", ip: "192.168.50.115"

  config.vm.synced_folder ".", "/vagrant", :disabled => true
  config.vm.synced_folder "fyler/", "/webapps/fyler", create: true, id: "vagrant-root",
    owner: "vagrant",
    group: "www-data",
    mount_options: ["dmode=775,fmode=764"]
end