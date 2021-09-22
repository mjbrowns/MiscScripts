#Miscellaneous Scripts
A variety of scripts I've written over the years that various people have suggested might be useful to others.

##brocadeparse
A simple tool to connect to a brocade FabricOS switch and parse its zoning configuration (aliases, zones, configurations) so they can be re-created easily on a new set of switches.  It is highly recommended to get ssh keys loaded on all the switches so you don't get prompted for the passwords a bunch of times

### Syntax
```bash
brocadeparse \<switch-FQDN\> [username]
```
_username defaults to "admin" if not specified_

### Example
To copy all zoning information from one switch to another, use the following, where switch1 = source switch, and switch2 = destination switch

```bash
brocadeparse switch1 | ssh admin@switch2
```

## sg_formatter
I do a lot of homelab stuff where I recycle trade-in equipment from work.  I often have to reformat SAS/SATA drives from 520byte to 512byte sectors.  In addition I often have to do secure type data wipes of the drives.  This tool enables it.  Use -h for help.  It's designed to be used with pipes so that you can identify and filter drives

### Example
```bash
sg_formatter -l |grep HITACHI| sg_formatter -f -m 
```

lists all detected drives, search for ones with the vendor HITACHI and pushes the result back in to be formatted and monitored through completion.
