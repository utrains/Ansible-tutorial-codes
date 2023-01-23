# -*- mode: ruby -*- 
# vi: set ft=ruby : 
VAGRANTFILE_API_VERSION = "2" 
Vagrant.configure(VAGRANTFILE_API_VERSION) do|config| 
    config.ssh.insert_key = false 
    config.vm.provider :virtualbox do|vb| 
        vb.customize ["modifyvm", :id, "--memory", "512"] 
    end 
    
    #Web Server 
    config.vm.define "ansible" do|ansible| 
        ansible.vm.hostname = "master" 
        ansible.vm.box = "geerlingguy/centos7" 
        ansible.vm.network "private_network", ip: "192.168.43.14" 
        ansible.vm.provision "shell", inline: <<-SHELL
        yum update -y
        yum install ansible vim -y
        SHELL
    end 
    
    #Application Server1 
    config.vm.define "app1" do|app| 
        app.vm.hostname = "webserver" 
        app.vm.box = "geerlingguy/centos7" 
        app.vm.network "private_network", ip: "192.168.43.11" 
    end 
    
    
    #Database Server 
    config.vm.define "db" do|db| 
        db.vm.hostname = "database" 
        db.vm.box = "geerlingguy/centos7" 
        db.vm.network "private_network", ip: "192.168.43.13" 
    end 
    
    
end

