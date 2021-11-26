# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.provision "shell", inline: <<SHELL
    sudo apt-get -y update
    # Install packages
    sudo apt-get -y install libarchive-tools python3 python3-pip python-is-python3

    # Install terraform
    curl -L https://releases.hashicorp.com/terraform/1.0.11/terraform_1.0.11_linux_amd64.zip | sudo bsdtar -xvf - -C /usr/local/bin/
    sudo chmod a+x /usr/local/bin/terraform
    
    # Install ansible
    sudo python -m pip install ansible

    # Install terraform-inventory
    sudo mkdir /etc/ansible
    sudo curl https://raw.githubusercontent.com/danielr1996/terraform-inventory/master/terraform.py -o /etc/ansible/terraform.py
    sudo chmod a+x /etc/ansible/terraform.py
    sudo tee /etc/ansible/ansible.cfg <<EOF
    [defaults]
    inventory=/etc/ansible/
EOF
SHELL
end