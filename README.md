# How To Use Vagrant With Libvirt KVM Provider
I'm using Ubuntu and I will install it to ubuntu. By default, Vagrant uses Oracle VirtualBox as provider,but I installed KVM and will try test it on this. 
#### First, you need to install KVM on your Linux system. 
```
sudo apt install libvirt-daemon-system libvirt-clients libxslt-dev libxml2-dev libvirt-dev zlib1g-dev ruby-dev ruby-libvirt ebtables dnsmasq-base
```
Paste command below and install **vagrant plugins**

```
vagrant plugin install vagrant-libvirt
```
For converting vagrant boxes to work with different providers we need to install **vagrant-mutate** 

```
vagrant plugin install vagrant-mutate
```

Ok, now we can just create a folder and **init** vagrant to in it. 

```
vagrant init centos/7
``` 
```
unity@unity:~/vagrant$ vagrant up
Bringing machine 'default' up with 'libvirt' provider...
==> default: Box 'centos/7' could not be found. Attempting to find and install...
    default: Box Provider: libvirt
    default: Box Version: >= 0
==> default: Loading metadata for box 'centos/7'
    default: URL: https://vagrantcloud.com/centos/7
==> default: Adding box 'centos/7' (v2004.01) for provider: libvirt
    default: Downloading: https://vagrantcloud.com/centos/boxes/7/versions/2004.01/providers/libvirt.box
Download redirected to host: cloud.centos.org
    default: Calculating and comparing box checksum...
==> default: Successfully added box 'centos/7' (v2004.01) for 'libvirt'!
==> default: Uploading base box image as volume into Libvirt storage...
==> default: Creating image (snapshot of base box volume).
==> default: Creating domain with the following settings...
==> default:  -- Name:              vagrant_default
==> default:  -- Description:       Source: /home/unity/vagrant/Vagrantfile
==> default:  -- Domain type:       kvm
==> default:  -- Cpus:              1
==> default:  -- Feature:           acpi
==> default:  -- Feature:           apic
==> default:  -- Feature:           pae
==> default:  -- Clock offset:      utc
==> default:  -- Memory:            512M
==> default:  -- Base box:          centos/7
==> default:  -- Storage pool:      default
==> default:  -- Image(vda):        /var/lib/libvirt/images/vagrant_default.img, virtio, 41G
==> default:  -- Disk driver opts:  cache='default'
==> default:  -- Graphics Type:     vnc
==> default:  -- Video Type:        cirrus
==> default:  -- Video VRAM:        16384
==> default:  -- Video 3D accel:    false
==> default:  -- Keymap:            en-us
==> default:  -- TPM Backend:       passthrough
==> default:  -- INPUT:             type=mouse, bus=ps2
==> default: Creating shared folders metadata...
==> default: Starting domain.
==> default: Domain launching with graphics connection settings...
==> default:  -- Graphics Port:      5902
==> default:  -- Graphics IP:        127.0.0.1
==> default:  -- Graphics Password:  Not defined
==> default:  -- Graphics Websocket: 5700
==> default: Waiting for domain to get an IP address...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 192.168.121.140:22
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: 
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default: 
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
==> default: Rsyncing folder: /home/unity/vagrant/ => /vagrant
```

I want to run a **centos7** virtual machine for testing **Ansible**

```
virsh
```
```
list --all
```
![img](/vagrant1/img/vagrant1.png)
![img](/vagrant1/img/vagrant2.png) 

Ok, it's ready for use 

By default, Vagrant VMs should be able to connect to internet via NAT. You don’t need to do any extra configuration. Just type **ip a** and connect via ssh. 

**username: vagrant**

**password: vagrant**


