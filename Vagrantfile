Vagrant.configure(2) do |config|

  config.vm.box = "debian/jessie64"
  config.vm.synced_folder ".", "/vagrant"
  ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
  config.vm.provision 'shell', inline: "echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys", privileged: false
  config.ssh.forward_agent = true
 
  config.vbguest.auto_update = false
  config.vbguest.no_remote = true

  config.vm.define "vm01" do |d|
    d.vm.network "private_network", ip: "192.168.0.101"
    d.vm.provider "virtualbox" do |vb|
      vb.memory = 1024 
    end
  end

  config.vm.define "vm02" do |d|
    d.vm.network "private_network", ip: "192.168.0.102"
    d.vm.provider "virtualbox" do |vb|
      vb.memory = 1024 
    end
  end

  config.vm.define "vm03" do |d|
    d.vm.network "private_network", ip: "192.168.0.103"
    d.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
  end
end
