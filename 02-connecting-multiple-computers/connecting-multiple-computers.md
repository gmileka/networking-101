# Connecting Multiple Computers

Connecting multiple computers together such that any computer can send and
receive data from any other computer involves several problems to solve.
The first problem is how we should physically connect the computers - and that
is what we will talk about in this article.

## Physically Connecting Multiple Computers

If we consider the electricity wiring in our homes, then, we know we can 'split'
the power line and that will allow us to plug-in more appliances to the same
power outlet! Of course, this has implications on the voltage and on the power
delivered to each appliance, along with the total power delivered.

Can we do the same with our network cables though?!

![Figure A](./basic-wiring.jpg)

[Figure A](./basic-wiring.jpg)

It is not that simple. We have to pay attention to the power and the voltages
across all our end-points and ensure that it meets the requirements of the
network adapters for a reliable communication.

To simplify the problem, each network adapter port has been designed to expect
a single receiver/sender on the other end of the wire. So, now, we just need
to design a device that is able to take signals from multiple wires and
replicate that signal unto one or more wires.

Enter the **network hub**.

![Figure B](./hub-wiring.jpg)

[Figure B](./hub-wiring.jpg)

A network hub is a device that has multiple ports, and it can replicate the
signal received from one port unto all the other ports - maintaining the signal
electrical characteristics (voltage, power, etc).

With that, any computer on our network can send data to any other computer on
the same network!

The above topology is considered a single **"network segment"**. A "network
segment" refers to a group of computers that are connected to the same physical
media.

Also note that because of how those computers are connected together, if one
computer emits a signal, all computers on the same network segment will
intercept that signal. Those computers receiving the signal constitute the
**"broadcast domain"** for the sender.

This group of computers along with these connections form a **"Local Area
Network"** or a **LAN** for short.

Note that the signal propagation is purely based on the physical connections -
this is the first level of networking and is called the **"Physical Layer"** or
**"Layer 1"** network.

Note that because the network hub just replicates the signal and sends it to
all computers on the network, all computers will get the same signal. How does
a computer know if the signal it is receiving is intended for it though?

Let's explore this together in the next article...

----

[Main Page](../README.md) | [Previous: Connecting Two Computers](../01-connecting-two-computers/connecting-two-computers.md) | [Next: The Hardware Identity](../03-hardware-identity/hardware-identity.md)