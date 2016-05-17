# Installing Ubuntu Server 16.04 LTS VM

[Download](http://www.ubuntu.com/download/server) Ubuntu Server 16.04 LTS.

Currently, in order for you first have to extract the kernel and initrd. OS X can't natively mount Linux live ISOs, so you have to run the following:

``` shell
xhyve-manager extract ~/Downloads/ubuntu-16.04-server-amd64.iso
open /tmp/tmp.iso
```

This will mount a disk `Ubuntu-Server 16`.

``` shell 
xhyve-manager create
```

This will invoke a series of prompts with which you can do the initial configuration for the virtual machine.

[![asciicast](https://asciinema.org/a/epd4ajqwi6pfcx7z6u5kqnhmx.png)](https://asciinema.org/a/epd4ajqwi6pfcx7z6u5kqnhmx)

Specify a CD to mount:

![CD](/images/draganddrop.gif)

At the end, you'll be prompted to edit the configuration. Type in `y` to invoke your favorite editor (well, whatever's set to your `$EDITOR`).

Once you've finished installation, change the boot options to these:

``` apacheconf
[boot]
kernel = boot/vmlinuz-4.4.0-21-generic
initrd = boot/initrd.img-4.4.0-21-generic
options = earlyprintk=serial console=ttyS0 acpi=off root=/dev/vda1 ro
```

