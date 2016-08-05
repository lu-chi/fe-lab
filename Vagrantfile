# -*- mode: ruby -*-
# vi: set ft=ruby :

#require_relative './vagrant/key_authorization'

Vagrant.configure('2') do |config|

#   url - if the box will be fetched doesn't already exist
#	config.vm.box_url = "http://files.vagrantup.com/precise32.box"
   	config.vm.box = 'ubuntu/trusty64'
    config.vm.synced_folder ".", "/vagrant" #, disabled: true

#  authorize_key_for_root config, '~/.ssh/id_dsa.pub', '~/.ssh/id_rsa.pub'
    {
        'fe01'   => '192.168.10.10',
#        'fe02'   => '192.168.10.11',
#        'fe03'       => '192.168.10.12',
    }.each do |short_name, ip|
        config.vm.define short_name do |host|
            host.vm.network 'private_network', ip: ip
            host.vm.hostname = "#{short_name}.felab.local"
        end
    end

#   config.vm.provision "ansible" do |ansible|
#       ansible.playbook = "site.yml"
#   end

    config.vm.provision "shell" do |shell|
        shell.path = "bootstrap.sh"
    end

end


