flashSD
=======

shell script that partition and flash an OS on an sdcard using a simple configuration file

The configuration file needs to be in the same directory as the script and be named profile.
It describe every part of the SDcard to be flashed in a trivial way:

On should create a list of variable named P1 to PN for each part to flash.
The format is the following:

PX="<offset>,<size>,<type>,<format>,<source>"
where all numbers are in M or k or bytes:
 - <offset>:	is the offset of the file or partition on the sdcard. Leave 'default' for auto calculation.
 - <size>:	is the size of the partition or file. The file will be truncated is size is smaller than filesize. Leave default for auto calculation.
 - <type>:	is the filesystem id. Add a * to tell the partition is bootable
 - <format>:	is [ file[.offset] | archive.[fs] | partition.[fs] ]
     	- <file>:	flash a raw file on no partition. the .offset is optional and allow to skip the begining of the file
     	- <archive>: 	format a new partition, mount it and extract the archive in it
     	- <partition>: 	create an empty partition (with or without fs)
     	- [fs]:		represents the extension used with mkfs. It is mandatory for archive and optional for partition
 - <source>:	is the file to flash
 - 'default':	means auto calculate


Some example for profiles will be added to the profiles directory. To not hesitate to contribute yours.
