Vagrant.configure("2") do |config|

  config.vm.define "web1" do |web1|
    #para importar este tipo de box, debemos correr -> vagrant box add nginx_lab package.box
    #el archivo pacakge.box no se encuentra en el repositorio porque es muy pesado
    web1.vm.box = "nginx_lab"
    web1.vm.hostname = 'web1'
    web1.vm.network :private_network, ip: "192.168.1.100"
    web1.vm.provision "file", source: "web1.conf", destination: "/home/vagrant/nginx.conf"
    web1.vm.provision "shell" do |s|
      s.inline = "cp /home/vagrant/nginx.conf /etc/nginx/nginx.conf"
      s.privileged = true
    end
  end

  config.vm.define "web2" do |web2|
    web2.vm.box = "nginx_lab"
    web2.vm.hostname = 'web2'
    web2.vm.network :private_network, ip: "192.168.1.101"
    web2.vm.provision "file", source: "web2.conf", destination: "/home/vagrant/nginx.conf"
    web2.vm.provision "shell" do |s|
      s.inline = "cp /home/vagrant/nginx.conf /etc/nginx/nginx.conf"
      s.privileged = true
    end
  end

  config.vm.define "rev_proxy" do |rev_proxy|
    rev_proxy.vm.box = "nginx_lab"
    rev_proxy.vm.hostname = 'rev-proxy'
    rev_proxy.vm.network :private_network, ip: "192.168.1.110"
    rev_proxy.vm.provision "file", source: "rev_proxy.conf", destination: "/home/vagrant/nginx.conf"
    rev_proxy.vm.provision "shell" do |s|
      s.inline = "cp /home/vagrant/nginx.conf /etc/nginx/nginx.conf"
      s.privileged = true
    end
  end
end
