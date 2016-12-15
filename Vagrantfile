Vagrant.configure("2") do |config|

  config.vm.define "xenial" do |xenial|
    xenial.vm.box = "ubuntu/xenial64"
    xenial.ssh.insert_key = true
    xenial.vm.network "private_network", ip:"10.2.3.41"
    xenial.vm.hostname = "xenial"
    xenial.vm.provision "shell",
      inline: "apt-get update && apt-get -y install ansible aptitude python --no-install-recommends"
    xenial.vm.provision "ansible" do |p|
      p.verbose = "v"
      p.limit = "all"
      p.playbook = "tests/test.yml"
      p.extra_vars = {
        "sshd_admin_net" => "0.0.0.0/0",
        "ssh_allow_groups" => "vagrant sudo ubuntu"
     }
    end
  end

 config.vm.define "yakkety" do |yakkety|
    yakkety.vm.box = "ubuntu/yakkety64"
    yakkety.ssh.insert_key = true
    yakkety.vm.network "private_network", ip:"10.2.3.42"
    yakkety.vm.hostname = "yakkety"
    yakkety.vm.provision "shell",
      inline: "apt-get update && apt-get -y install ansible aptitude python --no-install-recommends"
    yakkety.vm.provision "ansible" do |p|
      p.verbose = "v"
      p.limit = "all"
      p.playbook = "tests/test.yml"
      p.extra_vars = {
        "sshd_admin_net" => "0.0.0.0/0",
        "ssh_allow_groups" => "vagrant sudo ubuntu"
     }
    end
  end

  config.vm.define "centos" do |centos|
    centos.vm.box = "centos/7"
    centos.ssh.insert_key = true
    centos.vm.network "private_network", ip:"10.2.3.43"
    centos.vm.hostname = "centos"
    centos.vm.provision "ansible" do |p|
      p.verbose = "v"
      p.limit = "all"
      p.playbook = "tests/test.yml"
      p.extra_vars = {
        "sshd_admin_net" => "0.0.0.0/0",
        "ssh_allow_groups" => "vagrant sudo ubuntu"
      }
    end
  end

  config.vm.define "fedora" do |fedora|
    fedora.vm.box = "fedora/25-cloud-base"
    fedora.ssh.insert_key = true
    fedora.vm.network "private_network", ip:"10.2.3.44"
    fedora.vm.hostname = "fedora"
    fedora.vm.provision "shell",
      inline: "dnf -y install ansible"
    fedora.vm.provision "ansible" do |p|
      p.verbose = "v"
      p.limit = "all"
      p.playbook = "tests/test.yml"
      p.extra_vars = {
        "sshd_admin_net" => "0.0.0.0/0",
        "ssh_allow_groups" => "vagrant sudo ubuntu"
      }
    end
  end
end
