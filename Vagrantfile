Vagrant.configure("2") do |config|

  config.vm.box       = "precise64"
  config.vm.box_url   = "http://files.vagrantup.com/precise64.box"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "priv/ansible/fyler_dev.yml"
    ansible.inventory_path = "priv/ansible/dev_hosts"
    ansible.verbose = 'vv'
  end

  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.network "private_network", ip: "192.168.50.115"

  config.vm.synced_folder ".", "/vagrant", :disabled => true
  config.vm.synced_folder "fyler/", "/webapps/fyler", create: true, id: "vagrant-root",
    owner: "vagrant",
    group: "www-data",
    mount_options: ["dmode=775,fmode=764"]
end