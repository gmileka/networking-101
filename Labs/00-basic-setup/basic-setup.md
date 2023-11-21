# Basic Setup

## Overview

In order to experiment with computer networking, at a minimum, we need to
create multiple networks with multiple machines in each, and connect
the networks together and to the internet.

This is not feasible for the majority of us due to the cost of having such a
setup. However, this can be simulated using virtualization. We can create
virtual switches and virtual machines with virtual network cards and create
most of the networks we want!

This also mean that we need to learn a little bit about virtualization and how
to create and manage all those entities.

In the sections below, we will explore how two possible setups to get us
started:
- The physical host is running Linux.
- The physical host is running Windows Professional/Enterprise/Server.

## Linux Setup

For this setup, we will have the host machine running Linux (Ubuntu) and the
guest virtual machines running Azure Linux.

![baremetal-ubuntu.jpg](./baremetal-ubuntu.jpg)

[Baremetal Ubuntu Configuration](./baremetal-ubuntu.jpg)

Here are detailed walk-throughs on how do this setup:
- [Create Linux Host](./create-linux-host.md)
- [Create Azure Linux virtual machines](./create-ubuntu-vm.md)

## Windows Setup

If you have a machine with Windows Professioinal, Windows Enterprise, or
Windows Data Center, then you can create the same Linux setup discussed earlier
as a virtual machine running on the Windows host.

![baremetal-windows.jpg](./baremetal-windows.jpg)

[Baremetal Windows Configuration](./baremetal-windows.jpg)

Here are detailed walk-throughs on how do this setup:
- [Create Windows Host](./create-windows-host.md)
- [Create Linux VMs](./create-linux-vms.md)
- [Create Azure Linux virtual machines](./create-ubuntu-vm.md)