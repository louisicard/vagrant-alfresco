# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/wily64"
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.provision "shell", path: "setup.sh"
  
  config.vm.synced_folder "alfreco_shared_classes/", "/opt/alfresco/tomcat/shared/classes", id: "alfreco_shared_classes",
    owner: "root",
    group: "root",
    mount_options: ["dmode=775,fmode=664"]
    
  config.vm.synced_folder "alfreco_shared_lib/", "/opt/alfresco/tomcat/shared/lib", id: "alfreco_shared_lib",
    owner: "root",
    group: "root",
    mount_options: ["dmode=775,fmode=664"]
	
  config.vm.provider "virtualbox" do |vb|
     vb.customize ["modifyvm", :id, "--memory", "6144"]
	 vb.customize ["modifyvm", :id, "--cpus", "8"]  
     vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
     vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]            
     vb.customize ["modifyvm", :id, "--nictype1", "virtio"]
  end	
  
end
