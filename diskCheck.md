### linux command to check diskInformation:
1. df and du to check free/ used space *(based on the mount information)*
2. mtab give the mounted filesystem info and fstab give the moutable filesystem info that provide reference for the mount command when used without any parameters
3. smartd daemon could assist smartctl tool to check disk drive information *(whole disk info, no partition info)*
4. gparted /dev/sda print free unit MB *(will provide info about unallocated space)*
