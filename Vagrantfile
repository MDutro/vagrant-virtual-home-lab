#Vagrantfile
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

    config.vm.define "main" do |subconfig|
        subconfig.vm.box = "generic/ubuntu2004"
        subconfig.vm.hostname = "main"
        subconfig.vm.provider ENV['VAGRANT_DEFAULT_PROVIDER']
        subconfig.vm.network "private_network", type: "dhcp"

        subconfig.vm.provider ENV['VAGRANT_DEFAULT_PROVIDER'] do |vb|
            #vb.enable_virtualization_extensions = false
            vb.linked_clone = false
            #vb.vname = "ubuntu_cluster_main"
        end

        subconfig.vm.provision "ansible" do |ansible|
            ansible.verbose = "v"
            ansible.playbook = "master_playbook.yaml"
        end
    end
end