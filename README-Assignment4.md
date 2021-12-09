
# ASSIGNMENT 4

##  WORK DISTRIBUTION

### AISHWARYA RAVI
  * Ran assignment 3 code and took output for Nested paging 
  * Tested and verified the results
  * Documented the steps and results

### SHRUTHI SRINIVASAN
  * Switched KVM to shadow paging (ept=0)
  *	Ran assignment 3 code and took output for Shadow Paging 
  * Tested and verified the results
  * Documented the steps and results

# PREREQUISITES

Assignment 3 configurations needs to be set up.

 # STEP 1:
  * Open virt-manager and start virtual machine. Run case 3 from previous assignment (To print all exit type wise counts). 

  	* Execute dmesg for nested paging
 # STEP 2: 	

 * Execute following commands to switch from nested paging to shadow paging:  
	
   *	sudo rmmod kvm_intel && sudo rmmod kvm && sudo modprobe kvm && sudo modprobe kvm_intel ept=0
   *	Reboot

## Questions
2. What changed between the two runs (ept vs non-ept)

Solution: 
   ## Nested Paging
  * The vmexits for EPT_VIOLATION
  * The VM exits for EPT_MISCONFIG
   ## Shadow Paging 
   * The VM exits for INVALPG
   * Count of exits for reason CR_ACCESS increased.
   * Exit count seen for XSETBV


  
 



