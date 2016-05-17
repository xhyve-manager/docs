
# The Usual Extraction of Boot Images

Currently, in order to start a Linux live environment in xhyve, first have to extract the kernel and initrd from the ISO and pass them as arguments to `-f kexec`.

To do that, you have to do these steps:

OS X can't natively mount Linux live ISOs, so you have to run the following:

``` shell
xhyve-manager extract ~/Downloads/ubuntu-16.04-server-amd64.iso
open /tmp/tmp.iso
```

This will mount a disk `Ubuntu-Server 16`.

You'll then need to copy `vmlinuz` and `initrd.gz` from `/Volumes/Ubuntu-Server 16`.

If this seems like a lot of work, I agree! That's why I've bundled an ubuntu/16.04 *starter*, which is just a folder containing the kernel and init disks that are necessary. This is automatically configured when you choose the ubuntu starter kit. 

# Installing Ubuntu Server 16.04 LTS

[Download](http://www.ubuntu.com/download/server) Ubuntu Server 16.04 LTS.


## Creating an xhyve machine


``` shell 
xhyve-manager create
```

This will invoke a series of prompts with which you can do the initial configuration for the virtual machine.

[![asciicast](https://asciinema.org/a/epd4ajqwi6pfcx7z6u5kqnhmx.png)](https://asciinema.org/a/epd4ajqwi6pfcx7z6u5kqnhmx)


Choose the ubuntu 16.04 starter kit when you get to that part.

![starter](/images/starter.png)

Specify a CD to mount:

![CD](/images/draganddrop.gif)

At the end, you'll be prompted to edit the configuration. Type in `y` to invoke your favorite editor (well, whatever's set to your `$EDITOR`).

Once you've finished installation, change the boot options to these:

``` apacheconf
[boot]
kernel = /usr/local/share/xhyve-manager/ubuntu/16.04/boot/vmlinuz-4.4.0-21-generic
initrd = /usr/local/share/xhyve-manager/ubuntu/16.04/boot/initrd.img-4.4.0-21-generic
options = earlyprintk=serial console=ttyS0 acpi=off root=/dev/vda1 ro
```

