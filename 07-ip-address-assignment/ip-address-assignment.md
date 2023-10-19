# IP Address Assignment

## Overview

In the same way one can assign a name to a machine when it is being setup, one
can also assign an IP address to the machine in the same fashion. Because the
IP is assigned manually, it is called a static IP. This is in contrast to a
dynamic IP that is assigned automatically by another computer on the network.

## Static IPs

Static IPs are useful in cases where there is no infrastructure to assign IPs
automatically. They are also useful when the operator (the person setting up
the machine) wants predictable/pre-known IPs to use with other software
solutions.

When configuring a computer with a static IP, we need to first know which
network it will be part of, and what the subnet mask for that network is.
This will help us assign the computer an IP that is reachable by other
computers on that network. Should we assign an IP outside the allowed range,
other computers will not be able to reach it thinking it does not belong to
the same network.

### IP Assignment on Linux

On Azure Linux, there are multiple ways of assigning a static IP.

You can use `ifconfig` with the interface name. Note that the "interface name"
can be thought of as the name of the physical port on the network card.

```bash
ifconfig ens1f0np0 10.185.135.4 netmask 255.255.255.128 up
# where:
#   ens1f0np0
#                is the interface name.
#   10.185.135.4
#                is the IP address to assign.
#   netmask 255.255.255.128
#                is the subnet mask.
#   up
#                is a flag to bring the interface up and enable it.
```

A similar way to using `ifconfig` is using `ip` - which is the newer tool for
configuring network interfaces on Linux.

```bash
ip address add 10.185.135.4/25 dev ens1f0np0
# where:
#   dev ens1f0np0
#                is the interface name.
#   10.185.135.4
#                is the IP address to assign.
#   /25
#                is the subnet mask.
```


Another way of assigning static IPs, is to create a systemd network
configuration file for the target interface. For example:

```bash
# Create a configuration file
cat <<EOF >> /etc/systemd/network/10-static-ens1f0np0.network
[Match]
Name=ens1f0np0
[Network]
DHCP=no
Address=10.185.135.4/25
...
EOF

# Ensure it has the necessary permissions for the network stack to read it.
chmod 644 /etc/systemd/network/10-static-ens1f0np0.network

# Restart the network stack
systemctl restart systemd-networkd
```

Note that the `DHCP=no` is important to ensure that the network stack does not
try to assign an IP dynamically to this network interface.

## Dynamic IPs

Dynamic IPs are IPs that get assigned automatically by another computer on the
network. This computer is called a DHCP server. The DHCP server is first
configured with the range of IPs that is available (subnet mask), and when a
new computer wants to join the network, it broadcasts a request for an IP. The
request will get to all other computers on the network including the DHCP
server. The DHCP server will then respond with an IP from the available range
and mark it as taken in its internal database. The new computer will then
configure itself to use that new IP in all its network communications.

The program that is running on the new computer and requests an IP is the DHCP
client.

A computer can be configured to use a dynamic IP by configuring the DHCP client
to go through  the above process. On Azure Linux, this can be configured
through the systemd network interface configuration file as follows:

```bash
# Create a configuration file
cat <<EOF >> /etc/systemd/network/10-static-ens1f0np0.network
[Match]
Name=ens1f0np0
[Network]
DHCP=yes
...
EOF

# Ensure it has the necessary permissions for the network stack to read it.
chmod 644 /etc/systemd/network/10-static-ens1f0np0.network

# Restart the network stack
systemctl restart systemd-networkd
```

Note how we are configuring DHCP to be `yes` instead of `no` as we did in the
static IP configuration above.

## Definitions

| Term        | Description                                                                              |
|-------------|------------------------------------------------------------------------------------------|
| Interface   | A physical port on a network card.                                                       |