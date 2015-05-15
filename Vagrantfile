# -*- mode: ruby -*-
# vi: set ft=ruby :

RAM = ENV["VM_RAM"]
CPUS = ENV["VM_CPUS"]

Vagrant.configure(2) do |config|

  config.vm.box = "inclusivedesign/centos7"

  config.vm.provider :virtualbox do |v|
    v.customize ['modifyvm', :id, '--memory', RAM] if RAM
    v.customize ['modifyvm', :id, '--cpus', CPUS] if CPUS
  end
  
  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 8080 on the guest machine.
  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.synced_folder ".", "/vagrant"

  config.vm.provision "shell", inline: <<-SHELL
    sudo yum -y install ansible
    sudo sh -c "echo '[local]' > /etc/ansible/hosts"
    sudo sh -c "echo 'localhost' >> /etc/ansible/hosts"
    sudo sed -i 's/^transport.*/transport = local/g' /etc/ansible/ansible.cfg
    sudo sed -i 's/^#host_key_checking/host_key_checking/g' /etc/ansible/ansible.cfg
    sudo ansible-galaxy install -fr /vagrant/requirements.yml
    sudo ansible-playbook /vagrant/jenkins.yml
  SHELL

end
