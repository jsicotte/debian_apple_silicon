# Initialize Files
Create the varstore with and main drive with:

```
qemu-img create -f qcow2 varstore.img 64M
qemu-img create -f raw debian.raw 40G
```

Download debian for arm:

```
wget https://cdimage.debian.org/debian-cd/current/arm64/iso-dvd/debian-12.10.0-arm64-DVD-1.iso
```

Start the VM with the CD mounted:

```
start.sh
```

Once Debian in installed remove the cddrom line from start.sh.