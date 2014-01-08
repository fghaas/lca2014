# Kickstack: Rapid OpenStack Deployment with Puppet

Tutorial presented at the linux.conf.au 2014, Perth, WA, January 2014

This presentation is under the CC-BY-SA license, please consult the
[license file](LICENSE) for details.

This presentation uses
[reveal.js](https://github.com/hakimel/reveal.js/) with a custom
theme, with [shellinabox](http://code.google.com/p/shellinabox/) for
terminal emulation.

The terminal emulation parts **will not work** unless you have working
machines or VMs that you can connect to, with corresponding
shellinabox daemon. The demo VMs are not included in this repo and
have been made available to you separately.

# Setting up the demo environment

## Prerequisites

### VirtualBox

You'll need VirtualBox. It's available for Linux, Windows and Mac;
make sure you download and install the required packages.

### Virtual networks

The setup requires a total of 3 **host-only** networks (by default,
VirtualBox only installs one NAT network). On Linux and Mac, those
networks will be called vboxnet0, vboxnet1 and vboxnet2. On Windows,
they'll have a horribly long windozey.

For best results, you should configure your networks as follows:

* `vboxnet0`: 192.168.122.0/255.255.255.0, no DHCP
* `vboxnet1`: 192.168.133.0/255.255.255.0, no DHCP
* `vboxnet2`: 192.168.144.0/255.255.255.0, no DHCP

### SSH client

An SSH client like `ssh` or PuTTY would be helpful.

## Installing the `puppet` VM

Double-click on the `puppet.ova` file or select 
*File -> Import Appliance* from the VirtualBox manager (Ctrl-I might
also work). Select the `puppet.ova` file and import it. Make sure that
your first network adapter is connected to the NAT network, and your
second adapter is connected to `vboxnet0` (or, on Windows, the name of
your first host-only network adapter). When imported, boot the
VM. There is nothing else you need to do to it.

## Installing the OpenStack VMs

We will need **three** instances of the OpenStack VMs.

Double-click on the `puppet.ova` file or select 
*File -> Import Appliance* from the VirtualBox manager (Ctrl-I might
also work). Select the `openstack.ova` file and name it `alice` on
import. **Do check the "Reinitialize MAC Addresses" checkbox.**

Make sure that

* your first network adapter is connected to the NAT network;
* your second adapter is connected to `vboxnet0` (or, on Windows, the name of
your first host-only network adapter);
* your third adapter is connected to `vboxnet1` (or, on Windows, the name of
your second host-only network adapter);
* your fourth adapter is connected to `vboxnet2` (or, on Windows, the name of
your third host-only network adapter);

Then, boot the VM.

Finally, log in as `root` using the password `openstack` and run
`/root/fixup-host alice`. Then, reboot the box.

Repeat this process a second time, replacing both the hostname and the
`fixup-host` argument with `bob`.

Finally, repeat it a third time, replacing both the hostname and the
`fixup-host` argument with `charlie`.




