Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # Loop to create 3 managed nodes
  (1..3).each do |i|
    config.vm.define "node-#{i}" do |node|
      node.vm.hostname = "node-#{i}"

      # Assign static IP in the allowed VirtualBox range
      node.vm.network "private_network", ip: "192.168.56.10#{i}"

      node.vm.provider "virtualbox" do |vb|
        vb.name = "ansible-node-#{i}"
        vb.memory = 1024
        vb.cpus = 1
      end
    end
  end
end
