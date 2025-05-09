# Welcome To The World of PAIN
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
