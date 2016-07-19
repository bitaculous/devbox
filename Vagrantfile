#!/usr/bin/env vagrant

# All Vagrant configuration is done below. The `2` in `Vagrant.configure` configures the configuration version (we
# support older styles for backwards compatibility). Please don't change it unless you know what you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below. For a complete reference, please see the
  # online documentation at <https://docs.vagrantup.com>.

  # Every Vagrant development environment requires a box. You can search for boxes at <https://atlas.hashicorp.com/search>.
  config.vm.box = 'puppetlabs/debian-8.2-64-nocm'

  # Disable automatic box update checking. If you disable this, then boxes will only be checked for updates when the
  # user runs `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # The hostname the machine should have. Defaults to nil. If nil, Vagrant won't manage the hostname. If set to a string,
  # the hostname will be set on boot.
  config.vm.hostname = 'app.loc'

  # Create a private network, which allows host-only access to the machine using a specific IP.
  # config.vm.network 'private_network', ip: '192.168.10.10'

  # Create a public network, which generally matched to bridged network. Bridged networks make the machine appear as
  # another physical device on your network.
  # config.vm.network 'public_network'

  # Create a forwarded port mapping which allows access to a specific port within the machine from a port on the host
  # machine. Accessing `localhost:8080` will access port 80, and `localhost:8443` will access port 443 on the guest
  # machine.
  config.vm.network 'forwarded_port', guest: 80,  host: 8080, auto_correct: true
  config.vm.network 'forwarded_port', guest: 443, host: 8443, auto_correct: true

  # Share an additional folder to the guest VM. The first argument is the path on the host to the actual folder. The
  # second argument is the path on the guest to mount the folder. And the optional third argument is a set of
  # non-required options.
  config.vm.synced_folder 'craft',  '/home/vagrant/craft',  type: 'nfs'
  config.vm.synced_folder 'htdocs', '/home/vagrant/htdocs', type: 'nfs'
  config.vm.synced_folder 'log',    '/home/vagrant/log',    type: 'nfs'
  config.vm.synced_folder 'vendor', '/home/vagrant/vendor', type: 'nfs'

  # Provider-specific configuration so you can fine-tune various backing providers for Vagrant. These expose
  # provider-specific options.
  #
  # Example for VirtualBox:
  #
  # config.vm.provider :virtualbox do |vb|
  #   # Display the VirtualBox GUI when booting the machine.
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM.
  #   vb.memory = 1024
  # end
  #
  # Example for VMware Fusion:
  #
  # config.vm.provider :vmware_fusion do |vb|
  #   # Customize the amount of memory on the VM.
  #   vb.memory = 1024
  # end
  #
  # View the documentation for the provider you are using for more information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies such as FTP and Heroku are also available.
  # See the documentation at <https://docs.vagrantup.com/v2/push/atlas.html> for more information.
  #
  # config.push.define :atlas do |push|
  #   push.app = 'bitaculous/devbox'
  # end

  # Enable provisioning with a shell script. Additional provisioners such as Puppet, Chef, Ansible, Salt, and Docker are
  # also available. Please see the documentation for more information about their specific syntax and use.
  #
  # config.vm.provision :shell, inline <<-SHELL
  #   sudo apt-get install apache2
  # SHELL

  # Bootstrap the machine with the Ansible provisioner.
  config.vm.provision :ansible do |config|
    config.playbook = 'environment/playbook.yml'
  end

  # Picks up from any failed runs, run this with: `vagrant provision --provision-with resume`.
  # config.vm.provision :resume, type: :ansible do |config|
  #   config.playbook = 'environment/playbook.yml'
  #   config.limit    = '@environment/playbook.retry'
  # end
end