# Create Linux VMs - Cmd

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

# Using virt-install

```bash
mkdir mariner-vms
cd mariner-vms
wget https://aka.ms/mariner-2.0-x86_64-iso

mkdir mariner-vm-m0
cd mariner-vm-m0
sudo virt-install \
    --name mariner-vm-m0 \
    --memory 2048 \
    --vcpus 2 \
    --disk /home/george/mariner-vms/mariner-2.0-x86_64-iso,device=cdrom \
    --disk /home/george/mariner-vms/mariner-vm-m0/mariner-vm-m0.img,size=20 \
    --network default \
    --os-variant generic \
    --virt-type kvm \
    --boot uefi,loader_secure=no \
    --noautoconsole

    --location /home/george/mariner-vms/mariner-2.0-x86_64-iso \
    --boot uefi,loader=/usr/share/OVMF/OVMF_CODE_4M.fd,loader_secure=no \
    --machine pc-i440fx-hirsute \
    --os-type linux \ # deprecated

    ./run/libvirt/qemu/mariner-vm-m0.xml
    ./var/lib/libvirt/images/mariner-vm-m0.qcow2

Networking: NAT

virsh

virsh # list
 Id   Name              State
---------------------------------
 1    mariner-vm-m0     running

 virsh # console mariner-vm-m0

 follow the prompts...


 destroy vm-name
 undefine --nvram vm-name
```