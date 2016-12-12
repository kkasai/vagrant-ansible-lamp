Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.2"

  config.vm.network "forwarded_port", guest:80, host:80
  config.vm.network "forwarded_port", guest:3306, host:3306

  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # config.vm.network "private_network", ip: "192.168.33.10"

  # config.vm.synced_folder "../data", "/vagrant_data"

  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.verbose = "-vvv"
    ansible.extra_vars = {
      mysql: {
        user: "root",
        password: "root"
      }
    }
   end
end
