# Raspberry Pi System Configs
This project contains a set of system configurations for a local raspberry pi cluster.
The `.yml` files are intended to be run from ansible as a playbook.
Until main.yml is run, the setup will not be able to work with passwordless ssh

## Setting up the raspberry pi cluster.
The Raspberry pi cluster will be required to be set up manually.
All that will be required is the installation of the desired raspberry pi linux distro.
These ansible scripts have been tested and intended for a debian jessie release.

You'll need to set up your interfaces
`/etc/network/interfaces.d`

### eth1
```
auto eth1
allow-hotplug eth1
iface eth1 inet dhcp
```

### eth0
```
auto eth0
allow-hotplug eth0
iface eth0 inet static
  address: <your-address-here>
  netmask: <your-netmask-here>
  network: <your-network-here>
  broadcast: <your-broadcast-here>
```

restart and run `ansible-playbook dc-setup.yml -i inventory --ask-pass`

