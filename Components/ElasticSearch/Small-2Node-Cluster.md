# ElasticSearch Blueprint - Basic 2 Node Cluster #

## Overview ##
This blueprint describes the deployment of a 2 (VM) node cluster running ElasticSearch 1.4.

## Application Stack ##

### Operating System ###
CentOS 6.5

* Minimal install

### Software ###

* ElasticSearch 1.4.x
* Oracle Java 7
* NGINX 1.7


## Architecture ##
   
      =============                        =============
      | VM 1 (ES) |<---:Private Link:----->| (ES) VM 2 |
      |       |   |                        |  |        |
	  |(Web Proxy)|                        |(Web Proxy)|
      =============                        =============
            /\                                   /\
           /  \                                 /  \
	        ||                                   ||
		[HTTP/S]                             [HTTP/S]
	  :External Link:                     :External Link:
	        ||                                   ||
	  	    ||                                   ||
            

Notes:

* The 2 VMs are located on a private VLAN
* External connectivity is provided through NAT
* A Web Proxy is used to allow client traffic to:
** Use SSL to connect to the ES cluster
** Allow operators to connect to external authentication mechanisms using well tested modules


	  
