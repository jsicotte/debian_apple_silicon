# Welcome To The World of Pain
There are many guides out there that attempt to tell you how to run an ARM distro of Linux on an Apple Silicon based Macintosh. I have tried many of these but none seemed to really work well if at all. When you start to research this topic the guides tend to foll into several categories:
TODO fill out this area

# Getting Closer...
What really helped me was this article: https://theboreddev.com/run-ubuntu-on-mac-using-qemu/, this is the first guide to actually tell you how to do it with a display as well. The really important link in that article points to this GitHub repo that has EFI boot images that actuall work: https://gist.github.com/theboreddev/5f79f86a0f163e4a1f9df919da5eea20#file-qemu_efi-cb438b9-edk2-stable202011-with-extra-resolutions-tar-gz .

# Finaly, A Working Solution!
While the configuration in the article will indeed pull up a user interface, the keyboard and mouse inmput will not work. To fix this required one more addition:

```
-device qemu-xhci,id=xhci \
-device usb-kbd,id=keyboard,bus=xhci.0 \
-device usb-tablet,id=tablet,bus=xhci.0 \
```
Once that was added to the configuration then I could finally navigate the installer to start setting up Debian.

# How To Actually Run This
Ok so first you will need to create a hard drive for Debian, so run this command:

`qemu-img create -f qcow2 debian-3607-aarch64.qcow2 32G`

For those not that familiar with QEMU, this creates a file that will get larger as more disk space is used. This will continue until you reach the maxium of 32G.

Next download the DVD ISO file. Some use the net install, but I prefer to just download the whole distribution for the sake of speed and less moving parts.

`wget https://cdimage.debian.org/debian-cd/current/arm64/iso-dvd/debian-12.10.0-arm64-DVD-1.iso`

Once the ISO has finished downloading you can run the `./start.sh` which will launch QEMU with all the correct options. If everything worked correctly you should see this screen:

