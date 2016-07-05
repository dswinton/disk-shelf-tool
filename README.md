# disk-shelf-tool
Shelf Tool - CLI tool for managing JBOD disk shelves on Linux / Ubuntu.
Designed to make it quick and easy to identify which disks in your system are physically in each shelf and interact with them on a per-shelf basis.

Written for and tested on Ubuntu 16.04, but should work on any recent and similar Debian-esqe distro.



#Dependencies:
apt-get install sdparm php5-cli

For non-Debian-like distro's - you'll need your version of sas_blink_disk.
This tool uses the /dev/disk/by-id/ directory for discovery, so if your distro doesn't support this then this tool won't work.



# Usage: 
./shelf-tool <help|list|blink|deps|run> [shelf id] [command]



#Commands:

- help
-- displays this message

- list 
-- lists shelves (green) and their disks (red)
-- displays paths as /dev/disk/by-id/X

- list-sdx
-- lists shelves (green) and their disks (red)
-- Displays paths as /dev/sdX

- blink <shelf id> 
-- blinks all disks in a shelf

- run <shelf id> <command> 
-- runs a command on all disks in a shelf interactively, one at a time -- for example, use parted to format or partition disks



#Examples:


List disks in the system, grouped by shelf:
- ./shelf-tool list


Identify a shelf, or find out which disk(s) aren't being detected in a shelf:
- ./shelf-tool blink exp0x00000000000


Run parted interactively on each disk in a shelf (one by one) to create labels and partitions:
- ./shelf-tool run exp0x00000000000 parted



#Todo:
This project is not actively  being developed by me, so over to you Open Source Community...
- Display vendor / SAS enclosure number information for the shelves to make them easier to identify
- List size / vendor and/or partition information next to each disk



#Credits:
Written by David Swinton.

No external libraries used, but the heavy lifting is done by Linux, PHP and the sdparm package.


