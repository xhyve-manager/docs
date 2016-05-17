# [xhyve-manager](https://github.com/0x414A/xhyve-manager)

A simple utility to manage the lifecycle of [xhyve](https://xhyve.org) Virtual Machines on OS X 10.10 and above.

## Commands

* `xhyve-manager setup` - setup up the host machine's NFS.
* `xhyve-manager create` - Create a new virtual machine.
* `xhyve-manager start [machine-name]` - start a virtual machine (must be run as root)
* `xhyve-manager edit [machine-name]` - edit the virtual machine configuration.
* `xhyve-manager extract [path-to-iso]` - helper command to convert a Linux ISO to something OS X can read

## Installation

You need to be running OS X 10.10 and above.

To install:

``` shell
git clone https://github.com/xhyve-manager/xhyve-manager
cd xhyve-manager
make install
```

Then, you'll need to run `setup` to set up your host machine with the correct NFS configuration so as to be able to do 2-way sync of folders.

``` shell
sudo xhyve-manager setup
```

This will create an entry in `/etc/exports`:

```  
# BEGIN XHYVE
/Users -mapall=501 -network 192.168.64.0 -alldirs -mask 255.255.255.0
# END XHYVE
```

And (re)start `nfsd`
