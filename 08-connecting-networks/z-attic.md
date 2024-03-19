
A problem arises when a computer in a given network wants to send data to a
computer in a different network. If the source network is using 10.0.0.0/8
while the destination network is using 192.0.0.0/24, if a computer in the
source network sends data to 192.0.0.10, for example, it will never reach its
destination because the destination is not part of the network that computer
sees.

The typical solution here is that we designate a computer in our private
network to be responsible for receiving data destined for addresses outside
the private network. That computer has a second connection to the destination
network (or to a network that can reach the destination network), and can
forward such data to the destination network. A computer that can do this
function is called a **gateway**.

The gateway computer is typically implemented by having a computer with two
network adapters:
- one network adapter is connected to the private network.
- one network adapter is connected to the destination network.

Then, there is software that forwards data incoming from the first network
adapter to the second. That way, the traffic will be duplicated on the
destination network and will appear as if it originated on the destination
network.

There is a problem, however. If the original packet looked like this:
- Source: 10.0.0.20
- Destination: 192.0.0.10

When such packet appears on the destination network, it will be received and
processed by 192.0.0.10. But what address should be used to respond? The source
address is not part of the 192 network!

There are two ways to solve this problem. One is to install a gateway on the
192 network that knows how to route the 10.0.0.0/8 addresses. However, this
solution is rarely used as it requires destination networks to know about all
source networks and that is not feasible.
A better solution is to have the gateway on the 10.0.0.0/8 network
'impersonate' all the computers on that networks when forwarding traffic to the
destination networks. Basically, when the above packet is received by the
gateway computer, it will replace the source address 10.0.0.20 with 192.0.0.40,
where 192.0.0.40 is the gateway addresss on the destination network.
That way, when a response is generated, it will be destined to 192.0.0.40. When
the gateway receives the response, the gateway will need a way to know which
computer in our network is that response destined to.

One way for doing that, is for the gateway server to attach a part number with
the source, and then store that when a response comes for that port number, it
is to be mapped to the original source address.

This is called Network Address Translation - or NAT'ing.
