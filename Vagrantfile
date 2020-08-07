# -*- mode: ruby -*-

# vi: set ft=ruby :

boxes = [
    {
        :name => "nginx",
        :eth1 => "192.168.30.10",
        :script => "ansible/install_nginx.yml" 
    },

    {
        :name => "web1",
        :eth1 => "192.168.30.22",
        :script => "ansible/install_apache.yml" 
    },
    
    {
        :name => "web2",
        :eth1 => "192.168.30.23",
        :script => "ansible/install_apache.yml"
    }
]

Vagrant.configure(2) do |config|

  config.vm.box = "bento/centos-7.2"
  config.vm.synced_folder "ansible", "/vagrant"

  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.hostname = opts[:name]
      config.vm.network :private_network, ip: opts[:eth1]
      config.vm.provision :ansible do |ansible|
        ansible.playbook = opts[:script]
      end
    end
  end
end

'''

'''