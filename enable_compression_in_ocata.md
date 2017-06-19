# Instructions to enable Compression Feature on HPE 3PAR Cinder driver for Ocata in Openstack

## Pre-requisites

* 3PAR Inform Release 3.3.1.215 or greater
* Openstack Ocata Release 
* python-3parclient >= 4.2.3

Openstack Ocata Release contains Cinder code which does'nt have support for Compresssion for HPE Storage Arrays 

```
$ mkdir ~/hpe_cinder_ocata
$ git clone https://github.com/hpe-storage/cinder-ocata ~/hpe_cinder_ocata

# Rename the cinder folder on the devstack 
$ mv /opt/stack/cinder /opt/stack/cinder_old

# Create a new folder, and copy the HPE specific changes for Compression enablement.
$ mkdir /opt/stack/cinder
$ cp -R ~/hpe_cinder_ocata/* /opt/stack/cinder

# Restart the cinder services
```
## Notes for enableing compression on HPE 3PAR

*	Compression is supported on only SSD disks and 8k, 20k series 3PAR array.
* Minimium size of volume needed to enable compression is 16GB.
* A full provisioned volume cannot be compressed, if a compression is enabled and provisioning type requested is full,
the resulting volume defaults to thinly provisioned compress volume.
*	For enabling compression through cinder, user must add hpe3par:compression as a key in Volumes types extra spec.
Value for this key is a Boolean (true/false).
Ex: hpe3par:compression =true
