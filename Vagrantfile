Vagrant.require_version ">= 1.8.0"

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.ssh.username = "ubuntu"
  # config.ssh.password = "9a4ceb9b7c52a848bc7c970d"
  config.ssh.private_key_path = "~/.vagrant.d/insecure_private_key"
  # config.ssh.username = 'vagrant'
  # config.ssh.password = 'vagrant'

  # config.vm.box = "bento/ubuntu-16.04"
  config.vm.box = "ubuntu/xenial64"

  config.vm.define "tbnl-web-001" do |web| 
    web.vm.network :private_network, ip: "10.10.21.100"
    web.vm.provider "virtualbox" do |vb|
      vb.name = "tbnl-web-001"
      vb.memory = 512
      vb.cpus = 1
    end
  end
  
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "deploy/ansible/site.yml"
    
    ansible.host_vars = {
        "tbnl-web-001" => {
        },
    }
    ansible.groups = {
        "all" => ["web"],
        "web" => ["tbnl-web-001"],
        "all:vars" => {
          "stage" => "development",
        },
        "web:vars" => {
          "role" => "web",
        }
    }
  end
end
