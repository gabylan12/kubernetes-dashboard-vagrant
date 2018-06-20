Vagrant.configure(2) do |config|
  config.vm.box = "flixtech/kubernetes"
  config.vm.synced_folder "data", "/data"
  config.vm.network "forwarded_port", guest: 8001, host: 8001
  config.vm.network "forwarded_port", guest: 8080, host: 8080
  config.vm.network "forwarded_port", guest: 30000, host: 30000

  config.vm.provider "virtualbox" do |vb|
     vb.memory = "2028"
  end

  config.vm.provision "shell", inline: <<-SHELL
     kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
     sudo systemctl enable kube-proxy
     sudo service kube-proxy start
  SHELL
end
