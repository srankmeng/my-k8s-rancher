# Vagrant

### Install Vagrant
macos
```
brew tap hashicorp/tap
brew install hashicorp/tap/hashicorp-vagrant
```
[another os](https://developer.hashicorp.com/vagrant/install#macOS)

### Initialize the project
Create directory then run command line
```
vagrant init ubuntu/focal64
```

### Install a box
Create box
```
vagrant box add ubuntu/focal64
```
Able to install others that you want [Discover Vagrant Boxes](https://app.vagrantup.com/boxes/search)

### Config Vagrantfile
```
Vagrant.configure("2") do |config|
  config.vm.define "rancher" do |rancher|
    rancher.vm.box = "ubuntu/focal64"
    rancher.vm.hostname = "rancher"
    rancher.vm.network "private_network", ip: "192.168.10.20"
    rancher.vm.provider "virtualbox" do |vb|
      vb.memory = "8192"
      vb.cpus = "4"
    end
  end

  config.vm.define "master1" do |master1|
    master1.vm.box = "ubuntu/focal64"
    master1.vm.hostname = "master1"
    master1.vm.network "private_network", ip: "192.168.10.21"
    master1.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = "2"
    end
  end

  config.vm.define "worker1" do |worker1|
    worker1.vm.box = "ubuntu/focal64"
    worker1.vm.hostname = "worker1"
    worker1.vm.network "private_network", ip: "192.168.10.22"
  end

  config.vm.define "worker2" do |worker2|
    worker2.vm.box = "ubuntu/focal64"
    worker2.vm.hostname = "worker2"
    worker2.vm.network "private_network", ip: "192.168.10.23"
  end
end
```

จากนั้นรัน `vagrant up` เพื่อสร้าง vms เมื่อเรียบร้อยก็ config cluster ต่อได้เลย

### Vagrant cli
Custom Vagrantfile and start
- start `vagrant up`
- suspend `vagrant suspend` / `vagrant suspend {name}`
- shutdown `vagrant halt` / `vagrant halt {name}`
- reload `vagrant reload` / `vagrant reload {name}`
- destroy `vagrant destroy` / `vagrant destroy {name}`
- ssh `vagrant ssh` / `vagrant ssh {name}`
- show status `vagrant status`
- show global status `vagrant global-status`
- show config `vagrant ssh-config` / `vagrant ssh-config {name}`