Vagrant.require_version '>= 1.6.0'

unless Vagrant.has_plugin?("vagrant-hostmanager")
    puts '-------------------------------------------------------------------------------------'
    puts "\tvagrant-hostmanager is not installed! You need run:"
    puts "\tvagrant plugin install vagrant-hostmanager"
    puts '-------------------------------------------------------------------------------------'
    exit
end

unless Vagrant.has_plugin?("vagrant-bindfs")
    puts '-------------------------------------------------------------------------------------'
    puts "\tvagrant-bindfs is not installed! You need run:"
    puts "\tvagrant plugin install vagrant-bindfs"
    puts '-------------------------------------------------------------------------------------'
    exit
end

dir = File.dirname(File.expand_path(__FILE__))

require 'yaml'
require "#{dir}/puphpet/ruby/deep_merge.rb"
configValues = YAML.load_file("#{dir}/puphpet/config.yaml")
if File.file?("#{dir}/vagrant.yaml")
  custom = YAML.load_file("#{dir}/vagrant.yaml")
  configValues.deep_merge!(custom)
end
data = configValues['vagrantfile']

eval File.read("#{dir}/puphpet/vagrant/Vagrantfile-#{data['target']}")
