# Glossary

| Term                             | Description      |
|----------------------------------|------------------|
| Boradcast Domain                 | A group of computers that receives the signal by a sender without copying/re-sending the signal.  [[ref](./02-connecting-multiple-computers/connecting-multiple-computers.md)] |
| Data Frame                       | A sequence of bytes containing the data to be sent along with meta data necessary for the network transfer and delivery. [[ref](./01-connecting-two-computers/connecting-two-computers.md)] |
| Data Packet                      | Data Frame.      |
| DHCP Client                      | A service running on each computer that can communicate with a DHCP server, get an IP, and configure a network interface with that IP. [[ref](../07-ip-address-assignment/ip-address-assignment.md)]|
| DHCP Server                      | A service running on one computer in the network and keeps an inventory of available IPs. It can allocate IPs to other machines that request one. [[ref](../07-ip-address-assignment/ip-address-assignment.md)]|
| IP                               | Software network identity scheme consisting of a series of bytes. [[ref](./06-ip-addresses/ip-addresses.md)]                                           |
| IP Mask                          | The number of fixed bits in an IP addressing scheme and is used to indicate the range of the network that the address belongs to. [[ref](./06-ip-addresses/ip-addresses.md)] |
| IPv4                             | Software network identity scheme consisting of 4 bytes where each byte is written in decimal and is separated by a dot from the next. [[ref](./06-ip-addresses/ip-addresses.md)] |
| IPv6                             | Software network identity scheme consisting of 16 bytes where each 2 bytes are written in hexadecimal and are separated by a colon from the next pair. [[ref](./06-ip-addresses/ip-addresses.md)] |
| LAN (Local Area Network)         | The group of computers that are on the same network segment.  [[ref](./02-connecting-multiple-computers/connecting-multiple-computers.md)] |
| Layer 2 Communication            | Any communication that uses the MAC address of the network adapters to communicate with them.  [[ref](./05-vlans/vlans.md)]|
| Layer 3 Communication            | Any communication that uses the IP address assigned to a network adapter to communicate with it.  [[ref](./06-ip-addresses/ip-addresses.md)]|
| Network Adapter                  | Converts streams of bytes to analog signals on the network transfer medium. [[ref](./01-connecting-two-computers/connecting-two-computers.md)] |
| Network Interface                | A physical port on a network card. |
| Network Card                     | Network Adapter. |
| Network Hub                      | A device with multiple ports and is capable of replicating the signal received from one port unto all the other ports. [[ref](./02-connecting-multiple-computers/connecting-multiple-computers.md)] |
| Network Physical Layer (Layer 1) | The physical wire connections of the varios computers on the network.  [[ref](./02-connecting-multiple-computers/connecting-multiple-computers.md)] |
| Network Segment                  | A group of computers that share the same physical networking media/wire. [[ref](./02-connecting-multiple-computers/connecting-multiple-computers.md)] |
| Network Switch                   | A device that can replicate network signals unto other wire branches **selectively**.            |
| Subnet Mask                      | The bitwise mask for an IP addressing scheme where 1 indicates a fixed value for the network at hand, and 0 indicates a variable one. [[ref](./06-ip-addresses/ip-addresses.md)] |
| vLAN                             | A group of machines connected to a switch and isolated by software (running on the switch) from communicating with other physically connected machines to the same switch.  [[ref](./05-vlans/vlans.md)] |
| vLAN ID                          | A software identifier for the vLAN configuration. [[ref](./05-vlans/vlans.md)]                                               |

----

[Main Page](./README.md)