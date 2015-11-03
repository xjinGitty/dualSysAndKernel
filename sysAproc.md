### linux kernel interface for user to interact with kernel
1. /proc/ use the procfs interface, it just could export processing information
2. /proc/sys/ as a exception use the sysctl mechanism, that could used to modify kernel configuration parameter
3. /sys/ use sysfs, was designed to represent the whole device model as seen from the linux kernel *(it contains device driver and bus and their interconnection information)*
4. /sys/module, each kernel module loaded is represended with a directory

[procAsys](http://people.ee.ethz.ch/~arkeller/linux/multi/kernel_user_space_howto-2.html)
