
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  # config.vm.box = "centos/7"

  config.ssh.insert_key = false

  config.vm.define "head" do |head|
    head.vm.box = "bento/centos-stream-8"
    head.vm.hostname = "head"
    head.vm.network :private_network, ip: "192.168.56.2"
  end

  config.vm.define "fe1" do |fe1|
    fe1.vm.box = "bento/centos-stream-8"
    fe1.vm.hostname = "fe1"
    fe1.vm.network :private_network, ip: "192.168.56.3"
  end

  config.vm.define "node01" do |node01|
    node01.vm.box = "bento/centos-stream-8"
    node01.vm.hostname = "node01"
    node01.vm.network :private_network, ip: "192.168.56.101"
  end

  config.vm.define "node02" do |node02|
    node02.vm.box = "bento/centos-stream-8"
    node02.vm.hostname = "node02"
    node02.vm.network :private_network, ip: "192.168.56.102"
  end

  config.vm.define "node03" do |node03|
    node03.vm.box = "bento/centos-stream-8"
    node03.vm.hostname = "node03"
    node03.vm.network :private_network, ip: "192.168.56.103"
  end

  config.vm.define "node04" do |node04|
    node04.vm.box = "bento/centos-stream-8"
    node04.vm.hostname = "node04"
    node04.vm.network :private_network, ip: "192.168.56.104"
  end



  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080


  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end


  config.vm.provision "shell", inline: <<-SHELL
    if [ -f /vagrant/localenv.sh ]; then
      . /vagrant/localenv.sh
    fi
    dnf install -y http://repos.openhpc.community/OpenHPC/2/CentOS_8/x86_64/ohpc-release-2-1.el8.x86_64.rpm
    dnf config-manager --set-enabled powertools
     
    
    ansible-playbook -c local -i /vagrant/ansible/inventory/hosts -l $(hostname) /vagrant/ansible/site.yaml
  SHELL

end
