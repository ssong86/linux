**CMPE283 - Assignment 4**
**Sangwon Song**

**Q1.** For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched. (You may skip this question if you are doing the lab by yourself).

This part is skipped. I did the assginment by myself.

**Q2.** Include a sample of your print of exit ount output from dmesg from "with ept" and "without ept"

* Pre-condition: We need to use the Assignment 3 environment. I have the information about Assignment 1 in my linux github repository.	
	* Check the version of the linux kernel by `uname -r` command. It should be the same as Assignment 3.
		* In my case, it was `5.4.0-rc+1`. 	
	* Delete the kvm-intel module by ```rmmod kvm-intel```
	* Insert the module with ```ept=0```
		* ```insmod /lib/modules/5.4.0-rc+1/kernel/arch/x86/kvm/kvm-intel.ko ept=0```
* With ```ept=1``` screenshots
	* ```0x4ffffffd``` leaf for the total exit count for each exit type
	<img src="file:///home/song/Pictures/ept1-1.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept1-2.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept1-3.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept1-4.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept1-5.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept1-6.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept1-7.png" alt="drawing" width="500/">
	* ```0x4fffffff``` leaf for the total exit counts
	<img src="file:///home/song/Pictures/f-screen-edit.png" alt="drawing" width="500/">
	
* With ```ept=0``` (without ```ept```) screenshots
	* ```0x4ffffffd``` leaf for the total exit count for each exit type
	<img src="file:///home/song/Pictures/ept0-1.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept0-2.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept0-3.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept0-4.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept0-5.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept0-6.png" alt="drawing" width="500/">
	<img src="file:///home/song/Pictures/ept0-7.png" alt="drawing" width="500/">
	*```0x4fffffff``` leaf for the total exit counts
	<img src="file:///home/song/Pictures/ept0-f.png" alt="drawing" width="500/">
  

**Q3.** What did you learn from the count of exits? Was the count what you expected? If not, why not?
The result showed me the difference of the total exit counts and the total exit count for each exit type in the two different memory address translation technologies; Shadow Paging and Nested Pagng.
The count of exits with nested paging or ```ept=1``` is smaller than ones with shadow paging or ```ept=0```.
The result was the same as I expected because for generally speaking, shadow paging includes the page fault and TLB flushes whereas nested paging does not. Thus, I expected there would be more exits in shadow paging. Also, as we can check from the results, exits related to EPT are only enabled in nested paging. For example, exit 48 and 49, EPT violation and EPT misconfiguration, are only detected in nested paging. 



**Q4.** What changed between the two runs (ept vs no-ept)?
When I ran with ```ept=1```, nested paging enabled, and it generates exit counts less than shadow paging. As the question 3, EPT related exit reasons are only detectable in nested paging. 
With ```ept=0``` or without ```ept```, shadow paging enabled, and it generates more exit counts. The reason is that shadow paging includes page fault and TLB flushes whereas nested paging does not. 
	 	 