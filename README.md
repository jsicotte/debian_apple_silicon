# Overview
Trying to figure out how to run Debian in QEMU on an Apple Silicon based Mac was not trivial. When researching how to occomplish this I found that of the guides that sort of worked, none of them told you how to do it with a graphical installer. Since I wanted a graphical environment these would not work for me.
After a lot of research and experimentation I finally found the correct incantation that allows you to boot with a display and graphical install. Since this process was so painful I created this repository to help anyone else who might be facing the same challenge as me. 

# Saving Yourself Even More Time
For folks that do not want to go down this route I highly recommend using UTM. The authors of that software have figured out all the QEMU magic and everything (at least in my experience), works "out of the box". However, if you want the more manual approach then read on...

# Initialize Files
Create the varstore with and the drive that you will be installing Debian on with these commands:

```
qemu-img create -f qcow2 varstore.img 64M
qemu-img create -f raw debian.raw 40G
```

I have found that if you do not create the `varstore.img` then you can install Debain, but you will never be able to boot into it.


Download debian for arm:

```
wget https://cdimage.debian.org/debian-cd/current/arm64/iso-dvd/debian-12.10.0-arm64-DVD-1.iso
```
---

### Quick Note On The EFI Image

There are so many versions of this image floating around that I included the one that worked for me in this repo. It took me so long to find the "correct" image and I don't want anyone else to go through that pain.

---

Start the VM with the CD mounted:

```
start.sh
```

Once Debian in installed remove the cddrom line from start.sh.