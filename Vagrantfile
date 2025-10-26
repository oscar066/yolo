# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done within this Vagrant.configure block.
# The "2" indicates the configuration version.
Vagrant.configure("2") do |config|

  # 1. Define the Virtual Machine's Base Box
  # This line specifies which operating system image to use for our VM.
  # We are using Ubuntu 22.04 (Jammy Jellyfish).
  config.vm.box = "ubuntu/jammy64"

  # 2. Configure the Network for Port Forwarding
  # This allows us to access services running inside the VM from our host machine (your computer).
  
  # Forward port 80 in the guest VM (where the Nginx frontend container will listen)
  # to port 8080 on your host machine. You'll access the site at http://localhost:8080.
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Forward port 5000 in the guest VM (where the backend API container will listen)
  # to port 5000 on your host machine. This is useful for direct API testing.
  config.vm.network "forwarded_port", guest: 5000, host: 5000

  # 3. Configure the VM's Hardware Resources
  # It's important to allocate enough resources for the VM to perform well,
  # especially since we will be running Docker containers inside it.
  config.vm.provider "virtualbox" do |vb|
    # Allocate 2048 MB (2 GB) of RAM to the virtual machine.
    vb.memory = "2048"

    # Allocate 2 CPU cores to the virtual machine.
    vb.cpus = "2"
  end

  # 4. Configure the Ansible Provisioner
  # This block tells Vagrant to automatically configure the VM using Ansible
  # after it has been created and booted.
  config.vm.provision "ansible" do |ansible|
    # Specifies the path to our main Ansible playbook file. This path is
    # relative to the project's root directory (where this Vagrantfile is).
    ansible.playbook = "ansible-playbook/playbook.yml"

    # Automatically install Ansible on the guest VM if it's not already present.
    # This saves us from having to SSH into the box and install it manually.
    ansible.install = true

    # Ensure the latest version of Ansible is installed.
    ansible.version = "latest"
  end

end