# Adding WDS Onto Windows Server

1. In Server Manager on Windows Server, click on `Manage` and then `Add Roles and Features`.
2. In the `Before You Begin` page, click `Next`.
3. In `Select installation type`, select `Role-based or feature-based installation` and click `Next`.
4. In `Select destination server`, select `Select a server from the server pool` and select your chosen server. Mine will be this install of Windows Server which I have named `WinServer 2022`.
5. In `Select server roles`, look for and select `Windows Deployment Services` and click `Next`.
6. A new window should open called `Add Roles and Features Wizard`. Review everything and click `Add Features`.
7. Nothing needs to be done in `Select features`. Simply click `Next`.
8. In `Select role services`, make sure both `Deployment Server` and `Transport Server` are selected and then click `Next`.
9. Click `Install` to have WDS added to Windows Server

# Configure Server in Windows Deployment Services

1. Open `Windows Deployment Services` (WDS) either through the Server Manager or by searching it up using the built-in search bar.
2. On the left hand column of the WDS window, click on the arrow head to the left of `Servers` to expand it, showing your list of Windows servers. I only have one, which is the one I created earlier.
3. Right-click on the server you will be using to host/deploy your Windows image on and click on `Configure Server`.
4. On the `Before You Begin` page, read everything and click `Next`.
5. On the `Install Options` page, select the appropriate option that best describes your situation. Since the server I created is part of Active Directory and is the domain controller of this Active Directory, I selected `Integrated with Active Directory`.
6. The `Remote Installation Folder Location` asks you to select the path / location on a drive that will contain your images. Note that it is best practice (especially in a production environment) to NOT use the same volume that your Windows Server is installed on. For the purpose of this test, I decided to have the path be on the same drive/volume as my Windows Server.
7. On the `PXE Server Initial Settings` page, choose the most appropriate options. I have chosen `Respond to all client computers (known and unknown)`.
8. After, the configuration will be applied and you can either keep the check-box checked to add images to the server now or uncheck the box to do so at a later time and click on `Finish`.

# Adding Boot and Install Images

Once finished, you will notice several new folders have been created under your selected server. The two primary folders I will be focusing on will be `Install Images` and `Boot Images`. Before anything, make sure to mount your Windows disc file. Simply right click on the Disc Image File and click on `Mount`. This creates a new drive and gives us access to the files inside of the Disc Image.

1. Let's work with the `Boot Image` folder first. On the WDS window, fight click on `Boot Image` and click `Add Boot Image`.
2. If you known where the boot image file is located, you can type in the directory path for it. Otherwise, click on `Browse` and navigate to where the boot image file is located. This should be in the newly created drive when you mounted the Windows Disc Image earlier within the `Sources` folder. For example, my directory will be `E:\sources` where the E drive is the Disc Image File I mounted earlier. Select `boot.wim` and click `Next`.
3. Give the boot image a name and click `Next`.
4. Review the `Summary` page and click `Next` to add the boot image.
5. Right-click on `Install Images` folder in the WDS window and click `Add Install Image`.
6. Give the image group a name and click `Next`.
7. Locate the `install.wim` file like you did when locating the `boot.wim` file (it is in the same directory/location).
8. The `Available Images` page will provide you with a list of available Windows images that can install. Select the ones you want and click `Next`.
9. Review the `Summary` page and click `Next`.
10. Once done, you will see a list of available Windows images that can be installed.
