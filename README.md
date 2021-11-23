# WORK DISTRIBUTION 

   # AISHWARYA RAVI:
        # IMPLEMENTATION #
        
           * Configured a Linux machine in VMWare WorkStation.(Collaborated with each other)
           * Downloaded the Ubuntu disc image and installed in the VMWare WorkStation.(Collaborated with each other)
           * Built the Linux kernel source code.(Collaborated with each other)
           * Created a new kernel module with the assignment functionality.
           * Verified the output in the system message log.(Collaborated with each other)

   
        # ISSUES RESOLVED #:
        Resolved certificate and certificate related revocation errors faced during the execution of ** make -j <cpu num> ** command and fixed it by changing the values of following config keys (CONFIG_SYSTEM_TRUSTED_KEYS, CONFIG_SYSTEM_REVOCATION_KEYS) to empty string and disabled the config key CONFIG_DEBUG_INFO BIT for debugging related issues.
        
       
   # SHRUTHI SRINIVASAN:
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
![image](https://github.com/aishwaryaravi19/linux/blob/master/output/cmpe283.3.PNG)

# ASSIGNEMENT 2

# PRE REQUISITES
 Assignment 1 configuration is to be set up.

# STEPS FOLLOWED TO COMPLETE THE ASSIGNMENT

# STEP 1
 * Add code to KVM at file /linux/arch/x86/kvm/vmx/vmx.c and
   /linux/arch/x86/kvm/cpuid.c
   
 * For CPUID leaf node %eax= 0x4FFFFFFF:
     * Return the total number of exits (all types) in %eax.
 * For CPUID leaf node %eax= 0x4FFFFFFD:
     * Return the number of exits for the exit number provided (on input) in %ecx. The output should be returned in %eax.
  
 # WORKING CODE TO TEST THE FUNCTIONALITY
 
 # STEP 2
   Build the code
     * sudo make modules
     * sudo make modules_install
     * sudo make install
     * Reboot
     
 # STEP 3
   * Install Virtual Manager by using the following command: sudo apt-get install virt-manager
   * Open virt-manager and start virtual machine. Install CPUID package inside the inner vm.
     - sudo apt-get install cupid
     
 # STEP 4
  Execute the following code for case 1:
    * cpuid -l 0x4FFFFFFF
    
    
    * Execute dmesg command in the host system’s terminal
    
    
    * Total Exit count after rebooting
    
    
    * Total exits taken for VM reboot: 677887
    
   # STEP 5
  Execute the following code for case 3:
    * cpuid -l 0x4FFFFFFD s -12 (Exit 12)
    
    
    * Execute dmesg command in the host system’s terminal to count the exits available
    
    
    * Total Exit count after rebooting
    
    
    * Total exits taken for VM reboot: 677887  

# Questions
3. Comment of the frequency of exits

Answer: Frequency of the exits depends on the system use.The number of exit increases as more priveleged operations are performed.
       
4.Of the exit types defined in the SDM, which are the most frequent? Least?

Answer:  Most frequent exit - MSR_WRITE(count -605825)
         Least frequent exit - DR_ACCESS(count-8)
Most frequent exit is MSR_WRITE with count 605825






    
