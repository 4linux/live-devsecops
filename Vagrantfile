# -*- mode: ruby -*-
# vi: set ft=ruby :

vms = {
  'testing' => {'memory' => '2048', 'cpus' => 1, 'ip' => '50', 'box' => 'almalinux/8', 'provision' => 'provisionamento/testing.yaml'},
  'automation' => {'memory' => '2048', 'cpus' => 1, 'ip' => '60', 'box' => 'almalinux/8','provision' => 'provisionamento/automation.yaml'}
}

Vagrant.configure('2') do |config|

  config.vm.box_check_update = false

        if !(File.exists?('id_rsa'))
          system("ssh-keygen -b 2048 -t rsa -f id_rsa -q -N ''")
       end

  vms.each do |name, conf|
    config.vm.define "#{name}" do |k|
      k.vm.box = "#{conf['box']}"
      k.vm.hostname = "#{name}.4labs.devsecops"
      k.vm.network 'private_network', ip: "192.168.56.#{conf['ip']}"
      k.vm.provider 'virtualbox' do |vb|
        vb.customize ["modifyvm", :id, "--groups", "/LiveDevSecOps"]
        vb.name = conf["name"]
        vb.memory = conf['memory']
        vb.cpus = conf['cpus']
        
      end
      k.vm.provision 'ansible_local' do |ansible|
        ansible.playbook = "#{conf['provision']}"
      end
  end

  config.vm.provision "shell", inline: <<-SHELL
  sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
  systemctl restart sshd
  mkdir -p /root/.ssh
  cp /vagrant/keys/id_rsa /root/.ssh/id_rsa
  cp /vagrant/keys/id_rsa.pub /root/.ssh/authorized_keys
  chmod 600 /root/.ssh/id_rsa
  SHELL

  end
end