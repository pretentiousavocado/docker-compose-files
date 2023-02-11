# Debian  (Host Network)
## (etc/network/interfaces)
    # The primary network interface
    auto eth0.5
    iface eth0.5 inet static
    address 10.10.5.x
    netmask 255.255.255.0
    gateway 10.10.5.1
    dns-domain example.com
    dns-nameservers 1.2.3.4 5.6.7.8
    # A VLAN network interface based on a physical parent
    auto eth0.10
    iface eth0.10 inet manual


## Docker networking config example for ipvlan.
    docker network create -d ipvlan \
     --subnet=10.10.10.0/24 \
     --iprange=10.10.10.x/x \
     --gateway=10.10.10.1 \
     --attachable \
      -o ipvlan_mode=l2 -o parent=eth0.10 ipvlan10




Switch and/or vswitch uplink needs defined vlans tagged.