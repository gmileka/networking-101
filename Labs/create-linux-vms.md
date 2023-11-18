# Create Linux VMs

- Using the UX in Ubuntu, start `Virtual Machine Manager`.

![Figure A](virtual-machine-manager-0.JPG)

[Figure A](virtual-machine-manager-0.JPG)

- Create a new virtual machine

![Figure B](virtual-machine-manager-1.JPG)

[Figure B](virtual-machine-manager-1.JPG)

- Since we have downloaded the Mariner ISO, we will select `Local install media
  (ISO image or CDROM)`.

![Figure C](virtual-machine-manager-2.JPG)

[Figure C](virtual-machine-manager-2.JPG)

- Point Virtual Machine Manager to the ISO image and select `Generic or unknown
  OS. Usage is not recommended`. That is because Azure Linux has not been added
  to `Virtual Machine Manager`.

![Figure D](virtual-machine-manager-3.JPG)

[Figure D](virtual-machine-manager-3.JPG)

- Allocate memory and assign CPUs. For our exercises, we do not need much of
  either.

![Figure F](virtual-machine-manager-4.JPG)

[Figure F](virtual-machine-manager-4.JPG)

- Same for disk space, we do not need much space.

![Figure G](virtual-machine-manager-5.JPG)

[Figure G](virtual-machine-manager-5.JPG)

- Finally, let's give the virtual machine an easy to remember name.
- We will start with settin the Network selection to `Virtual network
  'default': NAT`. We will explain that setting later.

![Figure H](virtual-machine-manager-6.JPG)

[Figure H](virtual-machine-manager-6.JPG)


```bash

virt-install \
  --name mariner-vm-x3 \
  --memory 4096 \
  --vcpus 2 \
  --cdrom /home/george/mariner-vms/mariner-2.0-x86_64-iso \
  --disk size=8,bus=sata \
  --cpu host \
  --machine pc-i440fx-hirsute \
  --os-variant linux2020 \
  --network default \
  --boot cdrom,hd \
  --noautoconsole

  --boot uefi,loader=/usr/share/OVMF/OVMF_CODE_4M.fd,loader_secure=no \


```