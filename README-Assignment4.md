
# ASSIGNMENT 4

## Questions
1. For each member in your team, provide 1 paragraph detailing what parts of the lab that member 
implemented / researched.

Solution:

##  WORK DISTRIBUTION

### AISHWARYA RAVI
  * Verified that Assignment III code is functional.
  * Ran assignment 3 code and took output for Nested paging 
  * Tested and verified the results
  * Documented the steps and results

### SHRUTHI SRINIVASAN
  * Switched KVM to shadow paging (ept=0)
  * Ran assignment 3 code and took output for Shadow Paging 
  * Tested and verified the results
  * Documented the steps and results

## Together we analyzed the output and answered the questions
  
2. Include a sample of your print of exit count output from dmesg from “with ept” and “without ept”.

Solution: 

# PREREQUISITES

Assignment 3 configurations needs to be set up.

 # STEP 1:
  * Open virt-manager and start virtual machine. Run case 3 from previous assignment (To print all exit type wise counts). 

  * Execute dmesg for nested paging (i.e., with ept)
  
  ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment4/ASSIGNMENT 4 - IMAGE 1.png)
  
 # STEP 2: 	

 * Execute following commands to switch from nested paging to shadow paging:  
	
   *	sudo rmmod kvm_intel && sudo rmmod kvm && sudo modprobe kvm && sudo modprobe kvm_intel ept=0
   *	Reboot
 
 * Execute dmesg for shadow paging (i.e., without ept)
 
 ![image](https://github.com/aishwaryaravi19/linux/blob/master/output-assignment4/ASSIGNMENT 4 - IMAGE 2.png)

3. What did you learn from the count of exits? Was the count what you expected? If not, why not?

Solution: 

- In the case of shadow paging, we can observe from the output, maximum exit occurred of type “CR_ACCESS ".
- Also, INVLPG exit is present in case of shadow paging. INVLPG exit is used by hypervisor to invalidate translation in the TLB.

4. What changed between the two runs (ept vs non-ept)

Solution:

Nested Paging (ept=1)             |  Shadow Paging (ept=0)
----------------------------------| ---------------------------------
The VM exits for “EPT_VIOLATION”  | The VM exits for “INVALPG”
The VM exits for “EPT_MISCONFIG”  | Count of exits for reason “CR_ACCESS” increased significantly. Exit count seen for “XSETBV”
                                  
* In case of shadow paging the count of exits for reason “CR_ACCESS” increased significantly as hypervisor takes exits on access of CR register



