# Part 1: Hyper-V and Windows Server Setup

As an aside, this is also my first time using Hyper-V. As such, this is my first time setting up Hyper-V.

[Hyper-V](https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/about/) is Microsoft's hypervisor used to run virtual machines. Hyper-V is considered a type-1 hypervisor. It is a common misconception that Hyper-V is a type 2 hypervisor. Rather, once installed, Hyper-V becames a layer underneath the host OS. In other words, the host OS (the Windows installation you had) is now being virtualized.

# Installing Hyper-V

There are several ways to install Hyper-V, but I chose to stick to the GUI to do so this time. 

1. Go to `Control Panel` and navigate to `Programs and Features`.
2. On the left hand side of the window, click on `Turn Windows features on or off`. This will open up a new window
3. In this window, find Hyper-V and click on the checkbox to enable it
4. Press `Ok`. Your computer will need to be rebooted

# Setting up Hyper-V: vSwitch

With Hyper-V installed and your computer rebooted, open up Hyper-V Manager. The first thing to do is to set up a vSwitch. From experience, not doing so before setting up virtual machines will cause issues where the VMs would not have any sort of network connection.

1. On the main page of Hyper-V Manager, on the right hand side under the `Action` column, click on `Virtual Switch Manager`. <br>
<img src="https://github.com/user-attachments/assets/169aa281-9818-4f63-a48e-cf23970cb849" Width="700" /> <br>
2. A new window should open up that allows you to configure virtual switches. On the left hand column, select `New virtual network switch`. This then allows you to configure a new virtual switch on the right hand side. <br>
3. `External` should be select by default, but if not go ahead and select that. <br>
<img src="https://github.com/user-attachments/assets/b99d0170-50c0-48cd-bfc3-17665d09ee8b" Width="500" /> <br>
4. Click on `Create Virtual Switch`. This will add a new virtual switch on the left hand column. On the right hand colum will be the properties page of the selected virtual switch. In this case, it is the virtual switch that we just created. <br>
5. Provide a name for this new virtual switch. I have opted for the creatively named `External vSwitch`. <br>
6. Below you should see `Connection Type`. The virtual switch needs to be connected to a physical network card in order for the VMs using this vSwitch to be able to access the Internet. I have selected `External Network`, and having it point towards my system's network card. <br>
<img src="https://github.com/user-attachments/assets/f5bf8e82-45f8-4c5a-ba44-3a809abe2c07" Width="500" /> <br>
7. Click on `Apply` to save the changes made. You will receive a pop-up notice that applying these changes will disrupt your host system's network connectivity. <br>
<img src="https://github.com/user-attachments/assets/966c5337-9584-413a-b173-d4564d668f67" Width="500" /> <br>

# Creating a VM for Windows Server

The next step is to install Windows Server.

1. Back on the main page of Hyper-V Manager, under the `Actions` column, click on `New` and then select `Virtual Machine`. This opens up the wizard to configure a VM. <br>
<img src="https://github.com/user-attachments/assets/48789726-1777-43d1-b0c5-3f592602a50e" Width="500" /> <br>
2. The first page is the `Before You Begin` page. Read it and click `Next`. <br>
<img src="https://github.com/user-attachments/assets/7a63debd-fc7c-4486-b373-dd62bc74ff4b" Width="500" /> <br>
3. In `Specify Name and Location`, give the VM a name. I have opted to use `WinServer`. You can also choose where the VM will be stored as well. I am leaving it as is. <br>
<img src="https://github.com/user-attachments/assets/831abd2a-8720-4660-8522-a4adc1d8b5f6" Width="500" /> <br>
4. Under `Specify Generation`, choose either Generation 1 or Generation 2. This time, I chose Generation 1. <br>
<img src="https://github.com/user-attachments/assets/5eaa5c17-c141-41f4-bbfc-769a85f33095" Width="500" /> <br>
5. In `Assign Memory`, designate the amount of memory to be allocated for this VM. I have gone with `4096 MB`. <br>
<img src="https://github.com/user-attachments/assets/d6d1e6cd-8b4f-49d3-83aa-7ef4d89745a8" Width="500" /> <br>
6. In `Configure Network`, choose a network adapter. I am choosing the external switch I created earlier that I creatively named `External vSwitch`. <br>
<img src="https://github.com/user-attachments/assets/1c3e7874-9383-4eb6-8f9a-06e876be263e" Width="500" /> <br>
7. In `Create Virtual Hard Disk`, you will be creating a virtual hard disk that the OS will be intalled onto or to use an existing one. Since this is all a fresh setup, I have to create a new virtual hard disk. I also chose to allocate `60 GB` for this virtual hard disk as well. <br>
<img src="https://github.com/user-attachments/assets/bc445795-b433-4b9d-aa46-347729f55f1c" Width="500" /> <br>
8. In `Installation Options`, there are several options you can choose to install your OS from. Since I am using an .iso, I chose `Install an operating system from a bootable CD/DVD-ROM` and selected the .iso I will be using. <br>
<img src="https://github.com/user-attachments/assets/1e7153ee-f153-4bba-a5b4-b81ec9030912" Width="500" /> <br>
9. At the `Summary` page, click on `Finish` <br>
<img src="https://github.com/user-attachments/assets/ada3f54f-4c0d-49b1-8b14-e55d37acdd13" Width="500" /> <br>

Once all of the above is done, boot up the VM and go through the installer to have Windows Server installed. After installing Windows Server, setup Active Directory Domain Services and promote this Windows Server install as the domain controller.
