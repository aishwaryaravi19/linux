
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

  * Execute dmesg for nested paging (i.e., with ept)
  
 # STEP 2: 	

 * Execute following commands to switch from nested paging to shadow paging:  
	
   *	sudo rmmod kvm_intel && sudo rmmod kvm && sudo modprobe kvm && sudo modprobe kvm_intel ept=0
   *	Reboot
 
 * Execute dmesg for shadow paging (i.e., without ept)

## Questions

3. What did you learn from the count of exits? Was the count what you expected? If not, why not?

Solution: 
- In the case of shadow paging, we can observe from the output, maximum exit occurred of type “CR_ACCESS ".
- Also, INVLPG exit is present in case of shadow paging. INVLPG exit is used by hypervisor to invalidate translation in the TLB.

4. What changed between the two runs (ept vs non-ept)

Solution:

Nested Paging (ept=1)             |  Shadow Paging (ept=0)
----------------------------------| ---------------------------------
The VM exits for “EPT_VIOLATION”  | The VM exits for “INVALPG”
The VM exits for “EPT_MISCONFIG”  | Count of exits for reason “CR_ACCESS” increased significantly
                                  | Exit count seen for “XSETBV”

* In case of shadow paging the count of exits for reason “CR_ACCESS” increased significantly as hypervisor takes exits on access of CR register



