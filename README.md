This Github repository contains the configuration files necessary for setting up EVPN using Cumulus Linux and Quagga on the Reference Topology.

This demo is equivalent to the scenario in the MAC+IP Address learning section of the [BGP EVPN for VXLAN](https://cumulusnetworks.com/learn/web-scale-networking-resources/white-paper/Cumulus-Networks-White-Paper-EVPN_nY4KaJO/) whitepaper.  The whitepaper includes relevent commands to check the setup and operation of Cumulus EVPN.

The flatfiles in this repository will set up a BGP unnumbered along with the IPv4 and EVPN address family between the leafs and spines.  The servers will have a basic IPv4 and IPv6 configuration.  Server01 and 04 are in one VLAN/VXLAN, and servers 02 and 03 are in a different VLAN/VXLAN.

The demo shows the EVPN address family advertising MAC + IPv4 and MAC + IPv6 addresses with ARP suppression.

Quickstart: Run the demo
------------------------

Before running this demo, install VirtualBox and Vagrant. The currently supported versions of VirtualBox and Vagrant can be found on the [cldemo-vagrant](https://github.com/CumulusNetworks/cldemo-vagrant) page.

    git clone https://github.com/cumulusnetworks/cldemo-vagrant
    cd cldemo-vagrant
    vagrant up oob-mgmt-server oob-mgmt-switch 
    vagrant up leaf02 leaf03 spine01 spine02 server01 server02 server03 server04
    vagrant ssh oob-mgmt-server
    sudo su - cumulus
    git clone https://github.com/Diane-cumulus/EVPN_Cumulus_Whitepaper
    cd EVPN_Cumulus_Whitepaper 
    ansible-playbook deploy.yml
    ssh server01
    ping 172.16.20.4
    ping6 -I eth2 fd00::24





## Topology ##

This demo runs on a spine-leaf topology with four attached hosts. The ansible playbook deploy.yml requires an out-of-band management network that provides access to eth0 on all of the in-band devices. 

![EVPN Demo Topology](https://github.com/Diane-cumulus/EVPN_Cumulus/blob/master/EVPN_paper_diagram.png)



The following IP/IPv6 addresses are used on the hosts:
![Host Addressing Scheme](https://github.com/Diane-cumulus/EVPN_Cumulus/blob/master/EVPN_Host_Address_Table.png)
 


 

 


