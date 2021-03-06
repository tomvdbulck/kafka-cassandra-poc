# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	# Every Vagrant virtual environment requires a box to build off of.
	config.vm.box = "hashicorp/precise32"
	
	# Create a forwarded port mapping which allows access to a specific port
	# within the machine from a port on the host machine. In the example below,
	# accessing "localhost:8080" will access port 80 on the guest machine.
	# config.vm.network "forwarded_port", guest: 80, host: 8080
    config.vm.network :forwarded_port, guest: 9092, host: 9092   # kafka
    config.vm.network :forwarded_port, guest: 2181, host: 2181   # zookeeper
 
    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    config.vm.network "private_network", ip: "192.168.33.10"
    
	# Set virtual machine memory size
	config.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--memory", "1024"]
    end 
 
	config.vm.provision "shell", path: "vagrant/bootstrap-once.sh"
	config.vm.provision "shell", path: "vagrant/bootstrap-always.sh", run: "always"

    # remove tty errors in console
    config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
    
end
