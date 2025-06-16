ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'
Vagrant.configure("2") do |config|
    
    config.vm.define "node1" do |node1|
        node1.vm.box = 'ubuntu/jammy64'
        node1.vm.host_name = 'node1'
        node1.vm.network :forwarded_port, host: 2301, guest: 22        
        node1.vm.network "private_network", ip: "192.168.57.11", adapter: 2
        node1.vm.provider "virtualbox" do |vb|
            vb.memory = 2024
            vb.cpus = 2      
        end
        
        node1.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible_node1/provision.yml"
            ansible.inventory_path = "ansible_node1/hosts"
            ansible.host_key_checking = "false"
            ansible.limit = "all"
        end
    end

    config.vm.define "node2" do |node2|
        node2.vm.box = 'ubuntu/jammy64'
        node2.vm.host_name = 'node2'
        node2.vm.network :forwarded_port, host: 2302, guest: 22        
        node2.vm.network "private_network", ip: "192.168.57.12", adapter: 2
        node2.vm.provider "virtualbox" do |vb|
            vb.memory = 2024
            vb.cpus = 2      
        end
        
        node2.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible_node2/provision.yml"
            ansible.inventory_path = "ansible_node2/hosts"
            ansible.host_key_checking = "false"
            ansible.limit = "all"
        end
    end

    config.vm.define "barman" do |barman|
        barman.vm.box = 'ubuntu/jammy64'
        barman.vm.host_name = 'barman'
        barman.vm.network :forwarded_port, host: 2303, guest: 22        
        barman.vm.network "private_network", ip: "192.168.57.13", adapter: 2
        barman.vm.provider "virtualbox" do |vb|
            vb.memory = 2024
            vb.cpus = 2      
        end
        
        barman.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible_barman/provision.yml"
            ansible.inventory_path = "ansible_barman/hosts"
            ansible.host_key_checking = "false"
            ansible.limit = "all"
        end
    end
end