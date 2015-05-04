### bugs xjin reported that related with dual-boot or the partition or BIOS
https://bugzilla.suse.com/show_bug.cgi?id=873572
https://bugzilla.suse.com/show_bug.cgi?id=921466
https://bugzilla.suse.com/show_bug.cgi?id=885221
https://bugzilla.suse.com/show_bug.cgi?id=838536


### bios_gpt scenario:
https://bugzilla.novell.com/show_bug.cgi?id=872054
	  no GPT disk label?
	    => no checkbox visible at all, and no further action
	  booted with uEFI _and_ 'pmbr_boot' set on disk for '/boot/efi'?
	    => proposal to clear it (1)
	  booted legacy _and_ 'pmbr_boot' not set on disk for 'grub2-install'?
	    => proposal to set it (2)


### GPT (MBR)
1. protective MBR at LBA0 is used for protect the disk: for GPT non-supportted tools or os, will shown as unrecgonized type, except confirmly desire, will not allow to change the protected disk partitions; for GPT supported tools and os will check if the partition type in protective MBR is 0xEE, if not then modification will not be allowed.
2. in the Bios_boot scenario, Protective MBR also be used as the storage for the grub stage1; and modified as GPT recoganized.
3. hybrid MBR could be managed by gdisk tool and then GPT un-aware could use the up to 3 primary gpt partition and the GPT aware OS can use all the partions on the disk (used for BIOS based system)
	* use gdisk to make hybrid MBR and then install system (GPT aware and un-aware tool?)
	* how to create hybrid MBR (just resize the 0xEE partition size??)
	* [hibrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html)
	* usecase is: when BIOS+GPT dualsys for windows and linux, but windows do not support, so need hibrid MBR to help



### bootable flag
1. boot sector signature: for bios to recognize which disk could be used for boot up (bios see it as indicator if there is compatible bootloader in the boot sector, just as the below 5)
2. partition bootable flag: 0x80 at the very begining of the partition record: indicate loader which partition is bootable
3. windows loader need partition bootable flag, while grub could boot partition that without the bootable flag
4. some modern bios test if the bootable flag of at least one partition is set to start the bootcode from bios, although loader may do not need that flag
5. 55AA (little) or AA55 (big) boot signature indicate that there is IBM PC compatible bootload in the boot sector 


### 
