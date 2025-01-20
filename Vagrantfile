# -*- mode: ruby -*-
# vi: set ft=ruby :


server_ip="192.168.1.20"
bridge_interface="en0"

Vagrant.configure("2") do |config|
  config.vm.define "server" do |server|
    server.vm.box = "gyptazy/ubuntu22.04-arm64"
    server.vm.network "public_network", bridge: bridge_interface, ip: server_ip
    server.vm.provider "vmware_desktop"

    server.vm.provision :ansible do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.extra_vars = {
        server_ip: server_ip
      }
    end
  end
end