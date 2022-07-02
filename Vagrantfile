ENV["LC_ALL"] = "en_US.UTF-8"

# Master variables
K3S_MASTER = 3
K3S_MASTER_CPU = 1
K3S_MASTER_MEMORY = 1024
NETWORK_MASTER = "192.168.63.1"

# Worker variables
K3S_WORKER = 1
K3S_WORKER_CPU = 1
K3S_WORKER_MEMORY = 512
NETWORK_WORKER = "192.168.63.2"

# Add something here, if you want to modify the init script
$init_script = <<SCRIPT
    sudo apt update

    sudo apt install -y curl bash-completion \
        vim unzip
SCRIPT

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/focal64"

    (1..K3S_MASTER).each do |i|
        config.vm.define "k3s-master-#{i}" do |k3s_master|
            k3s_master.vm.hostname = "k3s-master-#{i}"
            k3s_master.vm.provider "k3s_master" do |vbox|
                vbox.cpu = K3S_MASTER_CPU
                vbox.memory = K3S_MASTER_MEMORY
            end
            k3s_master.vm.network :private_network, ip: "#{NETWORK_MASTER}#{i}", auto_config: true
            k3s_master.vm.provision "shell", inline: $init_script
        end
    end
end

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/focal64"

    (1..K3S_WORKER).each do |i|
        config.vm.define "k3s-worker-#{i}" do |k3s_worker|
            k3s_worker.vm.hostname = "k3s-worker-#{i}"
            k3s_worker.vm.provider "k3s_worker" do |vbox|
                vbox.cpu = K3S_WORKER_CPU
                vbox.memory = K3S_WORKER_MEMORY
            end
            k3s_worker.vm.network :private_network, ip: "#{NETWORK_WORKER}#{i}", auto_config: true
            k3s_worker.vm.provision "shell", inline: $init_script
        end
    end
end