---
layout: page
title: ERROR service ‚?‘ unknown or service sapms<SID> unknown
description: ERROR service ‚?‘ unknown or service sapms<SID> unknown
permalink: /:collection/:path
weight: 7
---

Please also have a look in our [OnlineHelp](https://help.theobald-software.com/en/) for further information.

It could be that you get the following error while connecting to SAP:
```
ERROR service ‚?‘ unknown
```
The problem is that there are sapdp* (eg. sapdp00  3200/tcp) entries missing in the file services in the folder `C:\Windows\System32\drivers\etc\services`

Please append the entries in the file *services* you can find at the bottom of this article to your services file.

If you get the 
```
ERROR service sapms<SID> unknown 
```
you have to append the following line to the file *services*. nn is the instance number of the SAP system (e.g. 00 or 99).
```
sapms<SID>  36<nn>/tcp  
```
For exapmle, if your SID is ECC for example, the line looks like the following one:
```
sapmsECC  3600/tcp  
```
For System ID (SID) ECC and instance number 12 please set:  
```
sapmsECC 3612/tcp
```
**IMPORTANT**<br>
When inserting this into this file, please ensure that the last entry is always terminated with a `return`. For some platforms, this may cause problems, as the last entry may not be recognized. 

**WARNING**<br>
The services file should not get any extension. The name should stay services and should not become e.g. services.txt 

After editing the file you may need to restart the Xtract service or the machine.   

[SAP Note 52959](https://launchpad.support.sap.com/#/notes/52959) 
