Vagrant.configure("2") do |config|
  

  config.vm.box = "ubuntu/xenial64"

  config.vm.define "balancer" do |balancer|
    balancer.vm.network "private_network", ip: "10.124.0.2"
    balancer.vm.network "forwarded_port", guest: 80, host: 8083
    balancer.vm.provider "virtualbox" do |vb|
        vb.memory = "512"
    end
  end

  config.vm.define "front1" do |front1|
    front1.vm.network "private_network", ip: "10.124.0.3"
    front1.vm.provider "virtualbox" do |vb|
        vb.memory = "512"
    end
  end

  config.vm.define "front2" do |front2|
    front2.vm.network "private_network", ip: "10.124.0.4"
    front2.vm.provider "virtualbox" do |vb|
        vb.memory = "512"
    end
  end

  config.vm.define "back" do |back|
    back.vm.network "private_network", ip: "10.124.0.5"
    back.vm.provider "virtualbox" do |vb|
        vb.memory = "512"
    end
  end

  config.vm.define "elk" do |elk|
    elk.vm.network "private_network", ip: "10.124.0.6"
    elk.vm.network "forwarded_port", guest: 5601, host: 8084
    elk.vm.provider "virtualbox" do |vb|
        vb.memory = "4096"
    end
  end

  config.vm.define 'controller' do |machine|
    machine.vm.network "private_network", ip: "10.124.0.17"

    machine.vm.provision :ansible_local do |ansible|
      ansible.playbook       = "playbook.yml"
      ansible.verbose        = true
      ansible.install        = true
      ansible.limit          = "all"
      ansible.inventory_path = "inventory"
    end
  end

end
