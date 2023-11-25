# Create Linux VMs

In this walk-through, we will create a virtual machine running Azure Linux
within our [Linux Host](../create-ubuntu-vm/create-linux-host.md).

Using the UX in Ubuntu, start `Virtual Machine Manager`:

![Figure A](virtual-machine-manager-0.JPG)

[Figure A](virtual-machine-manager-0.JPG)

Create a new virtual machine:

![Figure B](virtual-machine-manager-1.JPG)

[Figure B](virtual-machine-manager-1.JPG)

Since we have downloaded the Azure Linux ISO, we will select `Local install
media (ISO image or CDROM)`.

![Figure C](virtual-machine-manager-2.JPG)

[Figure C](virtual-machine-manager-2.JPG)

Point Virtual Machine Manager to the ISO image and select `Generic or unknown
OS. Usage is not recommended`. That is because Azure Linux has not been added
to `Virtual Machine Manager`.

![Figure D](virtual-machine-manager-3.JPG)

[Figure D](virtual-machine-manager-3.JPG)

Assign memory and CPUs. For our exercises, we do not need much of either.

![Figure F](virtual-machine-manager-4.JPG)

[Figure F](virtual-machine-manager-4.JPG)

Assign disk space...

![Figure G](virtual-machine-manager-5.JPG)

[Figure G](virtual-machine-manager-5.JPG)

Let's give the virtual machine a name that is easy to remember. Finally, we
will start with setting the Network selection to `Virtual network 'default': NAT`.
We will explain that setting later.

![Figure H](virtual-machine-manager-6.JPG)

[Figure H](virtual-machine-manager-6.JPG)

Once we click, `Finish` we shall have our first virtual machine running.

----

[Basic Setup](../basic-setup.md)