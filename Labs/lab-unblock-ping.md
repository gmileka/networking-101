# Unblock Ping

#### Machine Landscape

```bash

gmileka-main:
- 10.137.194.25

mariner-vm-m0:
- eth0: 192.168.122.241/24

mariner-vm-m1:
- etho0: 192.168.122.126/24


networking101host:
- etho0: 10.137.195.111
- virbr0: 192.168.122.1/24
```

#### Make an ubuntu machine ping-able

```bash
## use the specific iptables -A INPUT -p icmp -j ACCEPT
## and drop the following
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
```

#### Make a Linux machine ping-able

```bash
iptables -A INPUT -p icmp -j ACCEPT
```

