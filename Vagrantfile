# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "admin" , primary: true do |admin|
    admin.vm.box = "centos-6.5-x86_64"
    admin.vm.box_url = "https://dl.dropboxusercontent.com/s/np39xdpw05wfmv4/centos-6.5-x86_64.box"
    admin.vm.hostname = "admin.devires.com"
    admin.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=777"]
    admin.vm.synced_folder "/tmp/software", "/software"
    admin.vm.network :private_network, ip: "10.10.10.10"
    admin.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--name", "admin"]
    end
    admin.vm.provision :shell, :inline => "ln -sf /vagrant/puppet/hiera.yaml /etc/puppet/hiera.yaml"
    admin.vm.provision :puppet do |puppet|
      puppet.manifests_path    = "puppet/manifests"
      puppet.module_path       = "puppet/modules"
      puppet.manifest_file     = "site.pp"
      puppet.options           = "--verbose --hiera_config /vagrant/puppet/hiera.yaml"
      puppet.facter = {
        "environment"                     => "development",
        "vm_type"                         => "vagrant",
        "override_weblogic_user"          => "wls",
        "override_weblogic_domain_folder" => "/opt/oracle/wlsdomains",
      }
    end
  end

  config.vm.define "node1" do |node1|
    node1.vm.box = "centos-6.5-x86_64"
    node1.vm.box_url = "https://dl.dropboxusercontent.com/s/np39xdpw05wfmv4/centos-6.5-x86_64.box"
    node1.vm.hostname = "node1.devires.com"
    node1.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=777"]
    node1.vm.synced_folder "/tmp/software", "/software"
    node1.vm.network :private_network, ip: "10.10.10.100"
    node1.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1532"]
      vb.customize ["modifyvm", :id, "--name", "node1"]
    end
    node1.vm.provision :shell, :inline => "ln -sf /vagrant/puppet/hiera.yaml /etc/puppet/hiera.yaml"
    node1.vm.provision :puppet do |puppet|
      puppet.manifests_path    = "puppet/manifests"
      puppet.module_path       = "puppet/modules"
      puppet.manifest_file     = "node.pp"
      puppet.options           = "--verbose --hiera_config /vagrant/puppet/hiera.yaml"
      puppet.facter = {
        "environment"                     => "development",
        "vm_type"                         => "vagrant",
        "override_weblogic_user"          => "wls",
        "override_weblogic_domain_folder" => "/opt/oracle/wlsdomains",
      }
    end
  end
end
