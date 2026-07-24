Vagrant.configure("2") do |config|
  config.vm.box = "perk/ubuntu-2204-arm64"

  # Disable default auto-forwarding to prevent collisions
  config.vm.network "forwarded_port", guest: 22, host: 2221, id: "ssh", auto_correct: true

  # VM 1: Storage Node
  config.vm.define "node1" do |n1|
    n1.vm.hostname = "node1"
    n1.vm.network "private_network", ip: "192.168.56.11"
    n1.vm.provider "qemu" do |qe|
      qe.ssh_port = 2221
      qe.memory = "1024"
      qe.cpus = 1
    end
  end

  # VM 2: Compute Node
  config.vm.define "node2" do |n2|
    n2.vm.hostname = "node2"
    n2.vm.network "private_network", ip: "192.168.56.12"
    n2.vm.provider "qemu" do |qe|
      qe.ssh_port = 2222
      qe.memory = "2048"
      qe.cpus = 2
    end
  end

  # VM 3: Slurm Execution Node
  config.vm.define "node3" do |n3|
    n3.vm.hostname = "node3"
    n3.vm.network "private_network", ip: "192.168.56.13"
    n3.vm.provider "qemu" do |qe|
      qe.ssh_port = 2223
      qe.memory = "1024"
      qe.cpus = 1
    end
  end
end
