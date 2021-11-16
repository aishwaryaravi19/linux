# WORK DISTRIBUTION #

   # AISHWARYA RAVI #:
        # IMPLEMENTATION #
        
           * Configured a Linux machine in VMWare WorkStation.(Collaborated with each other)
           * Downloaded the Ubuntu disc image and installed in the VMWare WorkStation.(Collaborated with each other)
           * Built the Linux kernel source code.(Collaborated with each other)
           * Created a new kernel module with the assignment functionality.
           * Verified the output in the system message log.(Collaborated with each other)

   
        # ISSUES RESOLVED #:
        Resolved certificate and certificate related revocation errors faced during the execution of ** make -j <cpu num> ** command and fixed it by changing the values of following config keys (CONFIG_SYSTEM_TRUSTED_KEYS, CONFIG_SYSTEM_REVOCATION_KEYS) to empty string and disabled the config key CONFIG_DEBUG_INFO BIT for debugging related issues.
        
       
   # SHRUTHI SRINIVASAN #:
        # IMPLEMENTATION # 
        
           * Configured a Linux machine in VMWare WorkStation.(Collaborated with each other)
           * Downnladed the Ubuntu disc image and installed in the VMWare WorkStation.(Collaborated with each other)
           * Built the Linux kernel source code.(Collaborated with each other)
           * Loaded the new module
           * Verified the output in the system message log.(Collaborated with each other)
           
        # ISSUES RESOLVED #
         Resolved library related issues while executing make oldconfig command by installing packages for flex and bison.Also resolved issues while executing make prepare command.The execution was failing as libelf-dev and libncurses-dev were not configured in the ubuntu system.

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


# Issues faced during the execution #
    * Got an error while executing make oldconfig - Installed flex and bison libraries to resolve it
    * Got an error while executing make prepare - Installed  libelf-dev  and libncurses-dev to resolve all the package related issues.
    * Got an error while executing make -j <cpu num> - Changed the value of CONFIG_SYSTEM_TRUSTED_KEYS  and CONFIG_SYSTEM_REVOCATION_KEYS to empty string.
    * Got an error while executing make -j <cpu num> -   Disabled  CONFIG_DEBUG_INFO BIT
    
# Output #

![image](https://github.com/aishwaryaravi19/linux/blob/master/output/cmpe1.PNG)
![image](https://github.com/aishwaryaravi19/linux/blob/master/output/cmpe283.2.PNG)
![image](https://i.postimg.cc/7CfVDbR5/cmpe283-3.png)



    
