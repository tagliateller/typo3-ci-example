# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "chef/debian-7.4"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder ".", "/vagrant",
    type: "rsync",
    rsync__args: ['--links'],
    rsync__exclude: ".git/",
    owner: "www-data",
    group: "www-data"

  # Provision your virtual machine with ansible.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision.yaml"
    ansible.sudo = true
    ansible.raw_ssh_args = ['-o IdentitiesOnly=yes']
  end
end
