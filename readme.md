# kvm tools for testing openshift-windows
## Packet.net setup
Create a new c2.medium.x86 instance and choose centos7. During the create dialog, make sure to increase the number of ip's by going to the ssh-and-user-data tab
and choose /28 subnet

## KVM Setup on Centos 7
This is designed for use on Packet.Net EpyC Hardware as a service
  yum  install -y qemu-kvm qemu-img virt-manager libvirt libvirt-python libvirt-client virt-install virt-viewer bridge-utils
  yum install -y  "@X Window System" xorg-x11-xauth xorg-x11-fonts-* xorg-x11-utils -y
  yum install -y dhcp


## Setup the bonded bridge
Edit the bond0 ifcfg
 /etc/sysconfig/network-scripts/ifcfg-bond0  (Example in:  etc/sysconfig/network-scripts/ifcfg-bond0)

Add the Bridge
brctl addif br0 bond0
brctl show

Example:
[root@kvm kvm]# brctl show
bridge name	bridge id		STP enabled	interfaces
br0		8000.ec0d9abf3d58	no		bond0
							vnet0

## Setup dhcp
Add dhcp support to host for packet.net range
Example: etc/dhcp/dhcpd.conf

## Scripts

### initialvm.sh - Use o rhel75 iso to install a rhel 75 image
This script takes a rhel75 iso image of the complete os and creates a thin vm. Once its created, a subscription needs to be added, and any extranious rhn repos removed.
It should be set up to use dhcp.

