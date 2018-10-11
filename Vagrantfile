# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Box settings
  config.vm.define "centos" do |centos|
    centos.vm.box = "centos/7"
    centos.vm.box_download_checksum = "82275057cf0ddc37a7651065dd8f80ab2dda6023089a91513b422409a80343e4"
    centos.vm.box_download_checksum_type = "sha256"
    centos.vm.box_url = "https://cloud.centos.org/centos/7/vagrant/x86_64/images/CentOS-7-x86_64-Vagrant-1805_01.Libvirt.box"
    centos.vm.box_check_update = true
  end

  config.vm.define "debian" do |debian|
    debian.vm.box = "debian/stretch64"
  end

  # Network settings
  config.vm.synced_folder ".", "/vagrant", disabled: true # disables default behavior

  config.vm.provider :libvirt do |libvirt|
    libvirt.memory = 4096
    libvirt.graphics_type = "spice"
    libvirt.video_type = "qxl"
    libvirt.cpus = 4 # threads
    #libvirt.storage :file, :size => '110G', :device => 'vdb'
  end

  # Provisioning
  # config.vm.provision "shell", path: "bootstrap.sh"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
    #ansible.verbose = true
  end

end
