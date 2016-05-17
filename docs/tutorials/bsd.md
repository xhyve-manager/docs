# Installing FreeBSD 10.3

Download the [FreeBSD 10.3](ftp://ftp.freebsd.org/pub/FreeBSD/releases/amd64/amd64/ISO-IMAGES/10.1/) bootonly ISO.

Create a new machine:

``` shell 
xhyve-manager create
```

This will start a series of prompts where you can create a virtual disk and specify its size in GB, specify the name, etc.

Specify a CD to mount:

![CD](/images/draganddrop.gif)

Then you can start the machine:

``` shell
sudo xhyve-manager start [machine-name]
```

Once you've finished, edit the machine configuration to point `initrd` to the virtual disk to boot into the new FreeBSD virtual machine!

``` apacheconf
[boot]
kernel = /usr/local/share/xhyve-manager/userboot.so
initrd = /Users/aj/VDisks/F00E5442-5F2F-4FCF-AF95-40BAB28BFEAD.img
options =
```


