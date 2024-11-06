# Create a new VM and PXE Boot

1. Createa new VM. This new VM will be used to perform PXE boot. When creating this new VM, make sure that you also select `Generation 1` on the `Specify Generation` page and that you also select `Install an operating system from a network-based installation server.
2. Launch the newly created VM. The VM will immediately start to locate and connect to the server. When prompted to, press `F12` to start the installation of Windows through PXE boot. The `boot.wim` file will be loaded and you will be brought to the `Windows Setup` page.
3. Recall earlier when we were going through the WDS configuration wizard that we opted to allow the server to `Respons to all client computers (known and unknown)` and that if it is an unknown computer that admin approval is needed. Because this VM is an unkown computer, admin approval will be needed. Enter in the admin credentials:
4. Once admin access is given, go through the Windows installer wizard and Windows will start installing.
