VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.define "mysql" do |vagrant2|
        vagrant2.vm.provider "virtualbox" do |v|
          v.memory = 2048
        end
        vagrant2.vm.box = "ubuntu/trusty64"
        vagrant2.vm.hostname = "mysql.local"
        vagrant2.vm.network "forwarded_port", guest: 3306, host: 8306
        vagrant2.vm.network "private_network", ip: "10.10.10.21"
        vagrant2.vm.provision "ansible" do |ansible2|
            ansible2.playbook = "mysql.yml"
            ansible2.inventory_path = 'vagrant-inventory'
        end
    end
    config.vm.define "appserver" do |vagrant3|
        vagrant3.vm.provider "virtualbox" do |v|
          v.memory = 4096
        end
        vagrant3.vm.box = "ubuntu/trusty64"
        vagrant3.vm.hostname = "appserver.local"
        vagrant3.vm.network "forwarded_port", guest: 8080, host: 8181
        vagrant3.vm.network "private_network", ip: "10.10.10.31"
        vagrant3.vm.provision "ansible" do |ansible3|
            ansible3.playbook = "appserver.yml"
            ansible3.inventory_path = 'vagrant-inventory'
        end
    end
end
