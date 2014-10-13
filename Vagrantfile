#
# Osclass-Vagrant-Puppet LAMP stack
#

box      = 'precise32'
url      = 'http://files.vagrantup.com/precise32.box'
hostname = 'local'
domain   = 'osclass.dev'
ip       = '192.168.50.10'
ram      = '512'

Vagrant::Config.run do |config|
  config.vm.box = box
  config.vm.box_url = url
  config.vm.host_name = hostname + '.' + domain
  config.vm.network :hostonly, ip

  config.vm "virtualbox" do |v|
    v.customize[
      'modifyvm', :id,
      '--name', node[:hostname],
      '--memory', memory.to_s
    ]
  end

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = 'puppet/manifests'
    puppet.manifest_file = 'site.pp'
    puppet.module_path = 'puppet/modules'
  end
end
