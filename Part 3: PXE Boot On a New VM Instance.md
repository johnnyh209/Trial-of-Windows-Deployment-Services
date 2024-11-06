# Create a new VM and PXE Boot

1. Create a new VM. This new VM will be used to perform PXE boot. When creating this new VM, make sure that you also select `Generation 1` on the `Specify Generation` page and that you also select `Install an operating system from a network-based installation server`. <br>
<img src="https://github.com/user-attachments/assets/9bf74b81-483a-4d88-a5ff-3e149e55fa05" Width="500" />
<img src="https://github.com/user-attachments/assets/57acf7db-7cf3-4801-8315-4f4d209d7bb9" Width="500" /> <br>
2. Launch the newly created VM. The VM will immediately start to locate and connect to the server. When prompted to, press `F12` to start the installation of Windows through PXE boot. The `boot.wim` file will be loaded and you will be brought to the `Windows Setup` page. <br>
<img src="https://github.com/user-attachments/assets/2e26efea-15cb-4ada-8068-59ca4031f1f6" Width="500" /> <br>
<img src="https://github.com/user-attachments/assets/f73f69a2-8a2e-45ea-aae3-88dfce5bd74d" Width="500" /> <br>
4. Recall earlier when we were going through the WDS configuration wizard that we opted to allow the server to `Respons to all client computers (known and unknown)` and that if it is an unknown computer that admin approval is needed. Because this VM is an unkown computer, admin approval will be needed. Enter in the admin credentials: <br>
<img src="https://github.com/user-attachments/assets/02735466-1ab7-40bd-83ce-57c50cdfb1ea" Width="500" /> <br>
5. Once admin access is given, go through the Windows installer wizard and Windows will start installing. <br>
<img src="https://github.com/user-attachments/assets/4da073b8-179e-4e41-94f9-e431ec83bebc" Width="500" /> <br>
