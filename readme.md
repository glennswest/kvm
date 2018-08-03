# kvm tools for testing openshift-windows
## KVM Setup on Centos 7

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

Add dhcp support to host for packet.net range
Example: etc/dhcp/dhcpd.conf

## Scripts

### Initail Vm - Use o rhel75 iso to install a rhel 75 image

