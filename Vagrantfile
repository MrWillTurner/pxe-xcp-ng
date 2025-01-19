# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # config.vm.provider "vmware_desktop" do |v|
  #   v.gui = true
  # end


  config.vm.define "server" do |server|
    server.vm.box = "gyptazy/ubuntu22.04-arm64"
    server.vm.network "public_network", bridge: "en0", ip: "192.168.1.18"
    server.vm.provider "vmware_desktop"
    server.vm.provision "file", source: "xcp_ng", destination: "$HOME/xcp_ng"


    # vm1.vm.provision "shell", inline: <<-SHELL

    #   apt-get update
    #   # apt-get install -y isc-dhcp-server syslinux-common syslinux-efi tftpd-hpa lighttpd
    #   apt-get install -y isc-dhcp-server tftpd-hpa 
    #   # lighttpd syslinux-efi

      # mkdir -p /tftpboot/pxelinux.cfg
      # cp /usr/lib/syslinux/modules/efi64/{ldlinux.e64,libutil.c32,menu.c32} /tftpboot/
      # cp /usr/lib/SYSLINUX.EFI/efi64/syslinux.efi /tftpboot/

#       git clone git://git.ipxe.org/ipxe.git /tmp/ipxe
#       cat > /tmp/ipxe/src/chain.ipxe <<EOF
# #!ipxe

# dhcp
# chain http://192.168.1.18/EFI/xenserver/grubx64.efi
# EOF
#       cd /tmp/ipxe/src
#       make bin/undionly.kpxe EMBED=chain.ipxe
#       cp /tmp/ipxe/src/bin/undionly.kpxe /tftpboot/



#       mkdir /tftpboot/

#       cat > /etc/default/tftpd-hpa <<EOF
# TFTP_USERNAME="tftp"
# TFTP_DIRECTORY="/tftpboot"
# TFTP_ADDRESS=":69"
# TFTP_OPTIONS="--secure"
# RUN_DAEMON="yes"
# EOF
      


#       cat > /etc/default/isc-dhcp-server <<EOF
# INTERFACESv4="ens256"
# EOF

#       cat > /etc/dhcp/dhcpd.conf <<EOF
# subnet 192.168.1.0 netmask 255.255.255.0 {
#   range 192.168.1.150 192.168.1.200; 
#   option routers 192.168.1.1;
#   option domain-name-servers 8.8.8.8;
#   default-lease-time 600; max-lease-time 7200;
#   next-server 192.168.1.18;
#   filename "/EFI/xcp-ng/grubx64.efi";
#   }
# EOF

#   if exists user-class and option user-class = "iPXE" {
#       filename "http://192.168.1.18/EFI/xenserver/grubx64.efi";
#   } else {
#       option bootfile-name "snponly.efi";
#   }
# }
      # systemctl restart isc-dhcp-server

      # # wget http://boot.ipxe.org/snponly.efi

      # # mv snponly.efi /tftpboot/

      # mv  /home/vagrant/xcp_ng/* /tftpboot/

      # chmod -R 777 /tftpboot

#       cat > /etc/lighttpd/lighttpd.conf <<EOF
# server.document-root        = "/tftpboot"
# EOF

#       cat > /tftpboot/pxelinux.cfg/default <<EOF
# DEFAULT xcp-ng
# LABEL xcp-ng
#       KERNEL mboot.c32
#       APPEND xcp-ng/xen.gz dom0_max_vcpus=2 dom0_mem=2048M,max:2048M com1=115200,8n1 console=com1,vga --- xcp-ng/vmlinuz xencons=hvc console=hvc0 console=tty0 --- xcp-ng/install.img
# EOF
      # systemctl restart lighttpd
      # systemctl restart tftpd-hpa
      # docker pull ghcr.io/netbootxyz/netbootxyz
      # docker run -d \
      #   --name netbootxyz \
      #   -p 3000:3000 \
      #   -p 69:69/udp \
      #   -p 80:8080 \
      #   --restart unless-stopped \
      #   ghcr.io/netbootxyz/netbootxyz
#       apt-get install -y dnsmasq


#       # # Configure dnsmasq for DHCP and TFTP
#       cat > /etc/dnsmasq.conf <<EOF
#       listen-address=127.0.0.1#5300
#       interface=ens256
#       dhcp-option=3,192.168.1.1
#       dhcp-range=192.168.1.50,192.168.1.100,12h
#       dhcp-boot=netboot.xyz.kpxe
#       enable-tftp
#       #tftp-root=/var/lib/tftpboot
# EOF
#       systemctl restart dnsmasq
    # SHELL
  # end
  
    server.vm.provision :ansible do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end
end



     # Bring up a Docker container running the netboot server
    #  dhcp_range_start = ENV.has_key?("DHCP_RANGE_START") ? ENV["DHCP_RANGE_START"] : "192.168.0.1"

  #    vm1.vm.provision "docker" do |d|
  #     d.run "ghcr.io/netbootxyz/netbootxyz",
  #         args: "-e NGINX_PORT=80 -p 3000:3000 -p 69:69/udp -p 80:80 -v /home/vagrant/xcp-ng:/assets"
  #       # args: "--net=host --cap-add=NET_ADMIN -e DHCP_RANGE_START=" + dhcp_range_start
  #   end
  # end


  # config.vm.define "vm2" do |vm2|
  #   vm2.vm.box = "bento/ubuntu-20.04"
  #   vm2.vm.network "public_network", bridge: "en0", type: "dhcp"
  #   vm2.vm.provider "virtualbox" do |vb|
  #     vb.gui = true
  #     vb.customize ["modifyvm", :id, "--boot1", "net"]
  #     vb.customize ["modifyvm", :id, "--nic1", "none"]
  #   end
  #   # vm2.vm.box = ""
  #   # 
  # end
