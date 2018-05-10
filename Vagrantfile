$web1_script = <<-SCRIPT
cp /vagrant/web1/nginx.conf /etc/nginx/nginx.conf
cp /vagrant/web1/index.html /var/www/html/index.html
cp /vagrant/web1/index.php /var/www/html/index.php
SCRIPT

$web2_script = <<-SCRIPT
cp /vagrant/web2/nginx.conf /etc/nginx/nginx.conf
cp /vagrant/web2/index.html /var/www/html/index.html
SCRIPT

$rev_proxy_script = <<-SCRIPT
cp /vagrant/rev_proxy/nginx.conf /etc/nginx/nginx.conf
cp /vagrant/rev_proxy/index.html /var/www/html/index.html
SCRIPT


Vagrant.configure("2") do |config|
  # Prevent TTY Errors (copied from laravel/homestead: "homestead.rb" file)... By default this is "bash -l".
  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
    
  config.vm.define "web1" do |web1|
    #para importar este tipo de box, debemos correr -> vagrant box add nginx_lab package.box
    #el archivo pacakge.box no se encuentra en el repositorio porque es muy pesado
    web1.vm.box = "nginx_lab"
    web1.vm.hostname = 'web1'
    web1.vm.network :private_network, ip: "192.168.12.100"
    web1.vm.provision "shell" do |s|
      s.inline = $web1_script
      s.privileged = true
    end
  end

  config.vm.define "web2" do |web2|
    web2.vm.box = "nginx_lab"
    web2.vm.hostname = 'web2'
    web2.vm.network :private_network, ip: "192.168.12.101"
    web2.vm.provision "shell" do |s|
      s.inline = $web2_script
      s.privileged = true
    end
  end

  config.vm.define "rev_proxy" do |rev_proxy|
    rev_proxy.vm.box = "nginx_lab"
    rev_proxy.vm.hostname = 'rev-proxy'
    rev_proxy.vm.network :private_network, ip: "192.168.12.110"
    rev_proxy.vm.provision "shell" do |s|
      s.inline = $rev_proxy_script
      s.privileged = true
    end
  end
end
