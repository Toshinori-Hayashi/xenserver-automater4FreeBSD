## Create VM for a template

Create a VM for the base template in FreeBSD.

## Configure VM for base template

Add the following line to /etc/rc.conf.

    xe_auto_net_configure_enable="YES"

## Install startup scripts

Copy usr/local/sbin/xe-* into /usr/local/sbin/ and chmod +x

## Install network configuration scripts

Copy usr/local/etc/rc.d/xe_* into /usr/local/etc/rc.d/ and chmod +x

## Creating a template

    # xe vm-param-set uuid=VM_UUID is-a-template=true

## Create virtual machine

    # xe vm-install template=template_UUID new-name-label=VM_name
      OR
    # xe vm-install template=template_name new-name-label=VM_name

## Set up network information

    # xe vm-param-set uuid=NewVM_UUID xenstore-data:vm-data/ip=<IP address/192.168.0.XXX>
    # xe vm-param-set uuid=NewVM_UUID xenstore-data:vm-data/gw=<Default Gateway IP/192.168.0.1>
    # xe vm-param-set uuid=NewVM_UUID xenstore-data:vm-data/nm=<Netmask/255.255.255.0>
    # xe vm-param-set uuid=NewVM_UUID xenstore-data:vm-data/ns=<DNS Server IP/192.168.0.2>
    # xe vm-param-set uuid=NewVM_UUID xenstore-data:vm-data/dm=<DomainName/example.com>

## Start the virtual machine

    # xe vm-start uuid=NewVM_UUID
