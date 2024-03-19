# IP Address Known Ranges

## Overview

Each IP addressing scheme provides a range of addresses that can be assigned
to devices all over the world. If we are dealing with a private network, i.e.
a network that does not communicate with the internet, then, theoretically, we
pick any IP range and use it for the devices on our private network. We are
simply guaranteed that our range does not conflict with some other device that
is reachable from our network.

However, most networks we deal with and own are connected to other networks or
simply to the internet. As a result, we need to ensure that addresses assigned
to devices on our network are not in use by other devices on the networks we
are connected to and visible to us.

This would mean there needs to be a central authority for allocating and
assigning the addresses. Indeed, this is what the community have decided to do
and each country got assigned a range (see [IP ranges by country](https://lite.ip2location.com/ip-address-ranges-by-country)).

Due to the explosion in the number of devices connected to the internet, the
assigned address ranges were not enough to accommodate each country's need. To
solve this problem, several mechanisms have been developed that allow the
re-use of some address ranges - and yet avoid ambiguity at the same time.

One very popular mechanism is `Network Address Translation` or - `NAT`. In
this mechanism, the user has a private network, let's call it A, and the user
wants to connect it to a public network P (i.e. the internet). The user
designates one cmputer on network A to be a 'gateway'  to network P - that is;
a computer that is connected to both network A and network P and can forward
traffic from network A to network P. In other words, if any traffic originating


with one of its computers
designated as a gateway computer - that is; a computer that is connected to
both this private network (owned by the user), and to another network.
The gateway computer 'translates' the source addresses originating from the
private network to its own address and sends the data out. To 

When responses come back, that
computer knows how to unpack the data and route the responses back to the 
correct target computer in its own network.


## References

- [Reserved IP addresses](https://en.wikipedia.org/wiki/Reserved_IP_addresses).
- 