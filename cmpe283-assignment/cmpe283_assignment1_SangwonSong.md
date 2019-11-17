**CMPE283**
**Assignment 1**
**Sangwon Song**

**Q1.** For each member in your team, provide 1 paragraph detailng what parts of the lab that member implemented/researched. (You may skip this question if you are doing the lab by yourself).

* This part is skipped. I did the assignment by myself.

**Q2.** Describe in detail the steps you used to complete the assignment. Consider your reader to be someone skilled in software development but otherwise unfamiliar with the assignment. Good answers to this question will be recipes that someone can follow to reproduce your development steps.
**Note:** I may decide to follow these instructions for random assignments, so you should make sure they are accurate. 

* My environment was native Ubuntu (18.04 LTS).
* Forked Linux repository at [https://github.com/torvalds/linux](https://github.com/torvalds/linux) to a personal repository.
* Clone the repository to my local machine.
* Move to the directory `cd Linux`.
* Modify the source code for hypercall in `linux/arch/x86/kvm/x86.c`.
<img src="file:///home/song/Pictures/Screenshot%20from%202019-10-24%2015-03-10.png" alt="drawing" width=500>
The git diff file is also uploaded to my github.
* Install required library by the following commands:
```bash
apt-get install build-essential kernel-package fakeroot libncurses5-dev libssl-dev ccache bison flex libelf-dev -y
```
* Build kernel by the follwing commands.
```bash
make && make modules && make modules_install && make install
```
* Reboot the system by `reboot` command
* Check the kernel version by `uname -r` command. 
Mine changed from 4.15 to 5.4.0-rc1+
* Install virt-manager by the following command
```bash
apt-get install virt-manager
```
* Run virt-manager by `sudo virt-manager` and Install Ubuntu 18.04 LTS by an ISO file downloaded with your configuration.
 <img src="file:///home/song/Pictures/Screenshot%20from%202019-10-24%2015-22-33.png" alt="drawing" width="500/">
* Copy the test code in the virt-manager (guest VM) and run by the following commands
```bash
sudo apt get install gcc make
cd 283
make
sudo insmod cmpe283.ko
dmesg
```
* Check the result if it is the same as below
<img src="file:///home/song/Pictures/Screenshot%20from%202019-10-23%2002-06-57.png" alt="drawing" width="700"/>
Note: If you insert the module incorrectly, you will get the red commands.

**Q3.** What is the name of your github repo and URL? (Make sure you invite me to that repo – my github ID is mlarkin2015).
The name of github repo is **ssong86/Linux** and the URL is [https://github.com/ssong86/linux](https://github.com/ssong86/linux) 
I also invited mlarkin2015.
<img src="file:///home/song/Pictures/Screenshot%20from%202019-10-24%2015-40-32.png" alt="drawing" width="700"/>
