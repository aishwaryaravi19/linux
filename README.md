# STEPS FOLLOWED TO COMPLETE THE ASSIGNMENT #

* Download and install VMWare WorkStation 16
* Download Ubuntu 20.04.3 disc image.
* Configure Ubuntu in VMware Workstation.
* Allocate the resources as follows -
     * Memory - 8GB
     * Disk Space - 100GB
     * CPU - 8
* Fork the Linux repository on github account
* Clone the repository
* Create cmpe283-1.c using touch cmpe283-1.c command
* Modify the content as per as the requirement.
* cd Linux
* sudo apt-get install manpages-dev
* Copied the config file using cp /boot/config-5.11.0-38-generic .config
* Execute the following commands

     * make oldconfig
     * make prepare
     * make clean
     * make prepare
     * make -j 8 module
     * make -j 8
     * sudo make INSTALL_MOD_STRIP=1 modules_install
     * sudo make install
     * uname -a
     * sudo reboot
     * uname -a
     * make
     * sudo insmod cmpe283-1.ko
     * lsmod | grep cmpe283
     * Demsg


Issues faced during the execution -
Got an error while executing make oldconfig - Installed flex and bison libraries to resolve it
Got an error while executing make prepare - Installed  libelf-dev  and libncurses-dev to resolve all the package related issues.
Got an error while executing make -j <cpu num> - Changed the value of CONFIG_SYSTEM_TRUSTED_KEYS  and CONFIG_SYSTEM_REVOCATION_KEYS to null.
Got an error while executing make -j <cpu num> -   Disabled  CONFIG_DEBUG_INFO BIT
