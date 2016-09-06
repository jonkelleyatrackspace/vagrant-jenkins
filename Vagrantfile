# -*- mode: ruby -*-
# -*- coding: utf-8 -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # speeds up bad network
  config.vm.provider :virtualbox do |vb|
    # speedup
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  config.vm.box = "centos-7.0-x86_64"
  config.vm.box_url = "https://github.com/tommy-muehle/puppet-vagrant-boxes/releases/download/1.1.0/centos-7.0-x86_64.box"

  config.ssh.forward_agent = true
  config.ssh.insert_key = false
  # ------------
  # - DB NODE - 
  # ------------
  # Perform the api functions
  config.vm.define "jenkins" do |api|
    api.vm.hostname = "jenkins"
    api.vm.network :private_network, ip: "172.21.12.12", auto_config: true
    # The IP was reverting to dhcp... centos 7 issue?
    
    api.vm.network "forwarded_port", guest: 8080, host: 8888
    # http://stackoverflow.com/questions/32518591/centos7-with-private-network-lost-fixed-ip
    api.vm.provision :shell, :inline => "sudo nmcli connection reload", :privileged => true
    api.vm.provision :shell, :inline => "sudo systemctl restart network.service", :privileged => true

    api.vm.provision "ansible" do |ansible|
      #ansible.verbose = "vvvvv"
      ansible.playbook = "ansible-playbooks/jenkins.yml"
    end
  end
end