---
layout: post
section-type: post
title:  "Installing Linux Mint 17.1"
category: Linux
comments: true
tags: [ 'tutorial']
---

This walkthrough describes the installation of a linux distro called Mint 17.1 codename "Rebbeca" in a x64 laptop with OS windows. Therefore
we will need to use a virtual machine. In this walkthrough I used VirtualBox. 

## Installing **VirtualBox**

At this moment the last version is 4.3.28. Make sure to [download](https://www.virtualbox.org/wiki/Downloads) the correct package. 
For windows is the one that says **VirtualBox 4.3.28 for Windows hosts**

1. Run the executable previously downloaded.
2. Follow the instructions.

Easy peasy. Once finished run the Virtual machine.

## Creating a virtual machine

1. Click in the new button
2. Select Type: Linux and Version: Linux 2.6/3.x(64bit)

	![type](/assets/vm_type.png)

3. Select how much memory will be allocated for the virtual machine. I have plenty memory (8gb) although I will use the virtual machine just
writing some scripts and programming a bit. I think 2gb are enough and is less than the half of the green bar.

	![memory](/assets/vm_memory.png)

4. Create a new hard drive. Just select VDI if the point is to keep it simple.
5. Select how the virtual hard drive behave regarding to memory allocation. **Dynamically allocated** will grow automatically when more space is required 
(up to a maximum size), hence it will take processing time. **Fixed size** will allocate the memory since the installation of the virtual machine. I prefer 
to have the space allocated from the beginning due to I don't have problems with disc space and because I want it faster once running, so I chose fixed.

	![fixed](/assets/vm_hard_fixed.png)

6. Select the amount of space reserved for the virtual machine. It depends of the size of your hard drive. 20gb is fine for me.
7. After this, the virtual machine is created.

	![virtualdrive](/assets/vm_creatingvirtualdrive.png)

8. Hurray! I have a virtual machine.

	![virtualmachine](/assets/vm.png)

## Installing **Linux Mint**

1. Download the distro [here](http://www.linuxmint.com/download.php). It is a .iso which is a dvd image.
2. Click the *Start* button and select the .iso previously downloaded. And then start.

	![selectiso](/assets/mint_iso.png)
	
3. Once running Mint, run the Install Linux Mint icon. This will install the distro in the virtual machine.

	![mint_install](/assets/mint_first.png)
	
4. Follow the instructions keeping in mind the following screenshot. Just select Erase disk, this is a virtual machine, so don't be scared.

	![mint_erase](/assets/mint_erase.png)
	
5. Once finished the installation, finish it. That's it.

For more information about how to use VirtualBox follow this [link](https://www.virtualbox.org/wiki/End-user_documentation)