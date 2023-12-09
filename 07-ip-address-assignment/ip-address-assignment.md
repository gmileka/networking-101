# IP Address Assignment

## Overview

So, how does a computer get its IP address? Well, there are fundamentally two
ways; a user can assign a specific IP address to the computer, or the computer
itself can ask a central server for an IP address.

When the user assigns the IP address to a computer, it is called a
`static IP address` because it will not change unless the user explicitly
assigns a new one.

On the other hand, if the computer asks for the IP address, it is called a
`dynamic IP address` because it may change every time the computer asks for
a new IP address.

## Static IPs

Static IP addresses are useful in cases where either there is no infrastructure
to assign IP addresses automatically or the user setting up the machines
requires predictable IP addresses (for use with other software solutions, for
example).

When configuring a computer with a static IP address, we need to first know
what network switch it will be connected to. Based on the network switch, we
can find out the IP address ranges (or IP masks) that it is configured to
handle. Once we identify our target range (IP mask), we need to choose an IP
address that falls within that target range and has not been assigned to
another machine. Should we choose an IP address outside the ranges supported
by the network switch, the network switch will not forward the packages
correctly.

Each operating system has its own way of defining static IPs. Let's see
how Azure Linux allows its users to configure static IPs.

I will be preparing lab walk-throughs soon - but for now, let's just take a
quick look at how configuring a static IP address is done.

### Static IP Assignment on Azure Linux

On Azure Linux, there are multiple ways of assigning a static IP to a network
adapter (also called network interface).

First, we need to know the name of the network interface we are targeting.
We can achieve that by listing the detected interfaces using `ip a`:

```bash
ip a
1: lo:
   ...
2: eth0:
   ...
```

In this example, we have two network interfaces `lo` and `eth0`.

Then, one way to assign an IP is to use `ifconfig` with the interface name.
For example:

```bash
ifconfig eth0 10.185.135.4 netmask 255.255.255.128 up
# where:
#   eth0
#                is the interface name.
#   10.185.135.4
#                is the IP address to assign.
#   netmask 255.255.255.128
#                is the subnet mask.
#   up
#                is a flag to enable the interface.
```

Another way is to use `ip address add`. For example:

```bash
ip address add 10.185.135.4/25 dev eth0
# where:
#   dev eth0
#                is the interface name.
#   10.185.135.4
#                is the IP address to assign.
#   /25
#                is the subnet mask.
```

Finally, you can also assign IPs by creating a configuration file for the
target interface. For example:

```bash
# Create a configuration file
cat <<EOF >> /etc/systemd/network/10-static-eth0.network
[Match]
Name=eth0
[Network]
DHCP=no
Address=10.185.135.4/25
...
EOF

# Ensure it has the necessary permissions for the network stack to read it.
chmod 644 /etc/systemd/network/10-static-eth0.network

# Restart the network stack
systemctl restart systemd-networkd
```

Note that the `DHCP=no` is important to ensure that the network stack does not
try to ask for an IP address and assign to this network interface.

## Dynamic IPs

A computer can get a dynamic IP address by broadcasting on the network it is
connected to a request for an IP address. A given network should only have
a single computer running a software that:
- listens to such IP address requests.
- looks up the allowed range (network mask).
- finds an unused IP address in its own database.
- responds to the request with the unused IP addrress.

The computer/software is called the DHCP (Dynamic Host Configuration Protocol)
server. The computer who is asking for a dynamic IP address must be running a
DHCP client (to place the request, and to configure the machine with the IP
address in the response).

Before the DHCP server can respond to IP address requests, it must be first
configured with the range of IP addresses that are available (IP mask).

In the diagram below, Machine B wants an IP address for itself, so it
broadcasts a request. While both Machine A and Machine C receive the request,
only Machine A responds because it is the only machine running the DHCP server
and can hand out IP addresses.

![Figure A](./dynamic-ip.jpg)

[Figure A](./dynamic-ip.jpg)

### Dynamic IP Configuration on Azure Linux

To configure a specific network card to use dynamic IP addresses on Azure Linux,
you can run the following commands:

```bash
# Create a configuration file
cat <<EOF >> /etc/systemd/network/10-static-eth0.network
[Match]
Name=eth0
[Network]
DHCP=yes
...
EOF

# Ensure it has the necessary permissions for the network stack to read it.
chmod 644 /etc/systemd/network/10-static-eth0.network

# Restart the network stack
systemctl restart systemd-networkd
```

Note how we are configuring the `DHCP` property to `yes` instead of `no` as
we did in the static IP address configuration above.

## Reserved IP Address Ranges

Whether it is a static IP address assignment or a dynamic one, we need to
determine the IP range or IP mask. But who decides the IP mask for a given
network? Is it arbitrary? This is what we will talk about in our next article!

----

[Main Page](../README.md) | [Previous: vLANs](../06-ip-addresses/ip-addresses.md) | [Next: ]()