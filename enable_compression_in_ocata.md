# Instructions to enable 3PAR Compression Feature on Real Madrid Arrays in Openstack Ocata Release of Cinder

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
