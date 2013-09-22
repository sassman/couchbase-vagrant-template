# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Number of nodes to provision
  numNodes = 4

  # IP Address Base for private network
  ipAddrPrefix = "192.168.33.10"

  # Define Number of RAM for each node
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", 1024]
  end

  # Provision the server itself with puppet
  config.vm.provision :puppet

  # Download the initial box from this url
  config.vm.box = "ubuntu-server-1204-x64-vbox4210"
  # config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  # Provision Config for each of the nodes
  1.upto(numNodes) do |num|

    nodeName = ("node" + num.to_s).to_sym
    config.vm.define nodeName do |node|
      node.vm.box = "ubuntu-server-1204-x64-vbox4210"

      node.vm.network :private_network, ip: ipAddrPrefix + num.to_s
      node.vm.network :forwarded_port, guest: 8091, host: 8000 + num, auto_correct: true
      node.vm.network :forwarded_port, guest: 80, host: 9000 + num, auto_correct: true

      node.vm.provider "virtualbox" do |v|
        v.name = "Couchbase Server Node " + num.to_s
      end
    end
  end
end