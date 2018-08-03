### KVM Setup on Centos 7

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


