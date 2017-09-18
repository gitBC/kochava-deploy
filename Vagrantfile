Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network", ip: "192.168.10.20"
  #config.vm.synced_folder ".", "/var/www"

  config.vm.define "localvm"
  #
  # Run Ansible from the Vagrant Host
  #
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.groups = {
    	'development' => ["localvm"],
    	'go_server' => ["localvm"],
    	'php_server' => ["localvm"],
    	'redis_server' => ["localvm"],
    	'db_server' => ["localvm"]
    }
    ansible.raw_arguments = [
    	"-e env=development"
    ]
  end

end
