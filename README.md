#ubuntu ec2net utils

cp 53-ec2-network-interfaces.rules /etc/udev/rules.d

chmod 644 /etc/udev/rules.d/53-ec2-network-interfaces.rules

cp 75-persistent-net-generator.rules /etc/udev/rules.d

chmod 644 /etc/udev/rules.d/75-persistent-net-generator.rules

cp ec2dhcp /etc/dhcp/dhclient-exit-hooks.d/

chmod 644 /etc/dhcp/dhclient-exit-hooks.d/ec2dhcp

cp ec2net-functions /etc/network/

chmod 644 /etc/network/ec2net-functions

cp ec2net.hotplug /etc/network/

chmod 744 /etc/network/ec2net.hotplug
 
env INTERFACE=eth1 ACTION=add /etc/network/ec2net.hotplug add
 
ifup eth1
 
Port of Amazon's ec2-net-utils scripts to debian/ubuntu for automatically configuring AWS VPC interfaces
See: http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html#ec2-net-utils

see the copy.yml (ansible script) for a hint on how and where to install the files.

