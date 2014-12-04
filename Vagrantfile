# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
ROUTER_IP = '192.168.33.10'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "trusty64"
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"

  config.vm.network :private_network, ip: ROUTER_IP
  config.vm.network :forwarded_port, guest: 80, host: 8080

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.provision :ansible do |ansible|
    # Required to "warm up" the network
    # God knows why this is required
    # system("ping -c4 #{ROUTER_IP} > /dev/null")

    ansible.playbook = "setup-vagrant.yml"
    ansible.host_key_checking = false
  end
end
