Vagrant.require_version ">= 1.6.0"
VAGRANTFILE_API_VERSION = "2"

require 'fileutils'
require 'yaml'

nodes = YAML.load_file('nodes.yaml')

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false
  nodes.each do |node|
    config.vm.define node['hostname'] do |node_config|
      node_config.vm.box_check_update = false
      node_config.vm.hostname = node['hostname']
      node_config.vm.synced_folder '.', '/vagrant', :disabled => true
      node_config.vm.provider :digital_ocean do |digitalocean, override|
        override.ssh.username = 'core'
        override.ssh.private_key_path = '~/.ssh/id_rsa'
        override.vm.box = 'digital_ocean'
        override.vm.box_url = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"
        digitalocean.token = ENV['DIGITALOCEAN_TOKEN']
        digitalocean.ssh_key_name = ENV['DIGITALOCEAN_SSH_KEY_NAME']
        digitalocean.image = node['image']
        digitalocean.region = node['region']
        digitalocean.size = node['memory']
        digitalocean.setup = false
        digitalocean.private_networking = true
        digitalocean.user_data = File.read('user-data')
      end
    end
  end
end
