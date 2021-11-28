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

# WORK DISTRIBUTION

# AISHWARYA RAVI

   *	Created leaf node %eax= 0x4FFFFFFF for case I
   *	Changed cpuid.c and vmx.c to implement the functionality as mentioned in the assignment 2  
   *	Installed cpuid Pakage on inner VM
   *	Tested and Verified results
   *	Worked on the documentation.(Colloborated with Shruthi Srinivasan)


# SHRUTHI SRINIVASAN

  *	Created leaf node %eax= 0x4FFFFFFD for case III
  *	Changed cpuid.c and vmx.c to implement the functionality as mentioned in the assignment 2  
  *	Tested and verified results
  *   Worked on the documentation.(Collaborated with Aishwarya Ravi)


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
 
 # Modified cpuid.c
 
 ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/CMPE283.1.PNG)
 ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/CMPE283.2.PNG)
 ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/CMPE283.3.PNG)
 ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/CMPE283.4.PNG)
 ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/CMPE283.5.PNG)
 ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/CMPE283.6.PNG)
 
 # Modified vmx.c
  ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/CMPE283.7.PNG)
  ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/CMPE283.8.PNG)
 
 
 
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
     ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/Picture1.png)
    
    
    * Execute dmesg command in the host system’s terminal
    
     ![image] (https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/Picture2.png)
    
    
    
    * Total Exit count after rebooting
      ![image] (https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/Picture3.png)
     Total exits taken for VM reboot: 677887
    
   # STEP 5
  Execute the following code for case 3:
    * cpuid -l 0x4FFFFFFD s -12 (Exit 12)
     ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/ffffd-s1.png)
    
    
    
    
    * Execute dmesg command in the host system’s terminal to count the exits available
 ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/ffffd-s2.png)
    
    
    * Cpuid - I 0X4fffffffd -444 - output for invalid exit code 
   ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/ffffd-s3.png)
    
    
    
    * cpuid - I 0x4fffffffd s-3 - output for valid exit but not defined by KVM
   ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/ffffd-s4.png)  
    

# Questions

3. Comment of the frequency of exits
   Answer: Frequency of the exits depends on the system use.The number of exit increases as more priveleged operations are performed.
      ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/q3.png)
       
4.Of the exit types defined in the SDM, which are the most frequent? Least?

Answer:  Most frequent exit - MSR_WRITE(count -605825)
         Least frequent exit - DR_ACCESS(count-8)

![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment2/q4.png)


# ASSIGNMENT 3

##  WORK DISTRIBUTION

### AISHWARYA RAVI

### SHRUTHI SRINIVASAN

# PREREQUISITES

Assignment 1 configurations needs to be set up.

 # STEP 1:
Modify vmx.c and cpuid.c as per as the requirement.

 * For CPUID leaf node %eax= 0x4FFFFFFE:  
    * Return the higher 32 bits of the total time taken to  process all exits in %ebx
    * Return the lower 32 bits of the total time taken to process  all exits in %ecx
    * The values returned by %ebx and %ecx is measured across all VCPUs in every processor cycle.
  
 *	For CPUID leaf node %eax= 0x4FFFFFFC:
   * Return the time taken to process  the exit number provided (on input) in %ecx. 
   * Return the higher 32 bits of the total time taken to process  all exits in %ebx
   * Return the lower 32 bits of the total time taken to process  all exits in %ecx

 ### Code modified in vmx.c
 ### Code modified in cpuid.c
 
  # STEP 2
   Build the code
     * sudo make modules
     * sudo make modules_install
     * sudo make install
     * Reboot
     
   # STEP 3
  
   * Open virt-manager and start virtual machine. Install CPUID package inside the inner vm.
     - sudo apt-get install cupid

   # STEP4
     
      ### Case 2
       *	cpuid -l 0x4FFFFFFE
       
       
       *	Execute dmesg command in the host system’s terminal
       
       Total Exit count after rebooting 
       
       
       Total exits taken for VM reboot: 1486132839
       
   # STEP 5
     
       ### Case 4
 
         *	cpuid -l 0x4FFFFFFC s -32
         
         *	Execute dmesg command to view all the exits available count.
         
         * Cupid -l 0x4FFFFFFC s -444 to test the output for invalid exit code.
         
         * cupid -l 0x4FFFFFFC s -3 to test the output for valid exit but not implemented by KVM.








       











    
