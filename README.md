# pxe-xcp-ng

Vagrant/Ansible template to install XCP-NG via PXE.

This template will configure a VM with:
- DHCP server with PXE config : to offer an IP address to the client machine
- TFTP server: to host the grub image and xcp-ng install files 
- HTTP server: to host the answerfile 

This template is configured to use the vm image gyptazy/ubuntu22.04-arm64 and is then only usable on an arm64 artictecture (like Mac M1)




TODO:
- Add variables for answerfile IPs
- Add variables for DHCP network 