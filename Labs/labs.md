# Labs

## Machine Setup

In order to experiment with networking, we need multiple machines, and in some
cases multiple network cards in some of the machines. This is not feasible for
most of us at home without spending a considerable amount of money. Luckily,
we can learn a lot about networking by using virtualization. We can create
virtual switches and virtual machines with virtual network cards! The downside
is that we need to learn about how to create and manage them - which is not
essential to learning networking itself - but at least we learn something new
along the way.

With virtualization, we will use an Ubuntu Desktop environment. You can install
it directly on a physical machine or install it as a virtual machine on another
OS you already have.

If you have a machine with Windows Professioinal, Windows Enterprise, or Windows
Data Center, then you can create virtual machines/virtual switches. You can
follow the steps in [this article]() to get this setup.

Once you have the Ubuntu Desktop machine up and running, we will need to install
the virtualization stack.

- [Create Windows Host](./create-windows-host.md)
- [Create Linux Host](./create-linux-host.md)
  - [Create Linux VM](./create-ubuntu-vm.md)
- [Create Linux VMs](./create-linux-vms.md)

## Network Labs

- [Lab0: Unblock ping](./lab-unblock-ping.md)
