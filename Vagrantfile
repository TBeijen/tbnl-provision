Vagrant.require_version ">= 1.8.0"

Vagrant.configure("2") do |config|
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
    ansible.ask_vault_pass = true

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
