# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.provider :virtualbox do |v|
#    v.gui = true
    v.memory = 1024
#    v.linked_clone = true
  end

  config.vm.define "tomcat" do |app|
    app.vm.box = "centos/7"
    app.vm.hostname = "Tomcat"
    app.vm.network :private_network, ip: "192.168.33.13"
    config.vm.provider :virtualbox do |appv|
      appv.memory = 1024
      appv.cpus = 1
      config.disksize.size = '50GB'
  
    end
    config.vm.provision :ansible do |ansible|
      ansible.playbook = "playbook_roles.yml"
    end

  end

  config.vm.define "jenkins" do |app|
    app.vm.box = "centos/7"
    app.vm.hostname = "Jenkins"
    app.vm.network :private_network, ip: "192.168.33.14"
    config.vm.provider :virtualbox do |appv|
      appv.memory = 1024
      appv.cpus = 1
     config.disksize.size = '50GB'
    end
  end


  config.vm.define "gitlab" do |app|
    app.vm.box =  "centos/7"
    app.vm.hostname = "GitLab"
    config.disksize.size = '50GB'
    app.vm.network :private_network, ip: "192.168.33.12"
  end

  config.vm.define "artifactory" do |app|
    app.vm.box = "centos/7"
    app.vm.hostname = "Artifactory"
    app.vm.network :private_network, ip: "192.168.33.11"
    config.vm.provider :virtualbox do |appv|
      appv.memory = 1024
      appv.cpus = 1
      config.disksize.size = '50GB'
    end
  end

end

