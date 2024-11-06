# Adding WDS Onto Windows Server

1. In Server Manager on Windows Server, click on `Manage` and then `Add Roles and Features`. <br>
<img src="https://github.com/user-attachments/assets/24a85694-ef1c-4a3b-b63f-1416f20fcc25" Width="500" /> <br>
2. In the `Before You Begin` page, click `Next`. <br>
<img src="https://github.com/user-attachments/assets/148bac9d-c9a2-4642-a974-4e6bf2318cd1" Width="500" /> <br>
3. In `Select installation type`, select `Role-based or feature-based installation` and click `Next`. <br>
<img src="https://github.com/user-attachments/assets/5cbbe83d-7b64-4ab9-8d9b-df847135816c" Width="500" /> <br>
4. In `Select destination server`, select `Select a server from the server pool` and select your chosen server. Mine will be this install of Windows Server which I have named `WinServer 2022`. <br>
<img src="https://github.com/user-attachments/assets/08d037a8-9981-404e-85cb-064cc91076d2" Width="500" /> <br>
5. In `Select server roles`, look for and select `Windows Deployment Services` and click `Next`. <br>
<img src="https://github.com/user-attachments/assets/c1dcefe4-9abe-4bb8-8315-d47180923086" Width="500" /> <br>
6. In `Select role services`, make sure both `Deployment Server` and `Transport Server` are selected and then click `Next`. <br>
<img src="https://github.com/user-attachments/assets/3f07b54d-3cc2-4f74-bfe9-2ebabaa80e6f" Width="500" /> <br>
7. Click `Install` to have WDS added to Windows Server

# Configure Server in Windows Deployment Services

1. Open `Windows Deployment Services` (WDS) either through the Server Manager or by searching it up using the built-in search bar.
2. On the left hand column of the WDS window, click on the arrow head to the left of `Servers` to expand it, showing your list of Windows servers. I only have one, which is the one I created earlier.
3. Right-click on the server you will be using to host/deploy your Windows image on and click on `Configure Server`. <br>
<img src="https://github.com/user-attachments/assets/922689f4-732f-495d-b943-51b59161c2d7" Width="500" /> <br>
4. On the `Before You Begin` page, read everything and click `Next`. <br>
<img src="https://github.com/user-attachments/assets/7f9d4e5c-5569-4b16-a60c-efe9822dcc6e" Width="500" /> <br>
5. On the `Install Options` page, select the appropriate option that best describes your situation. Since the server I created is part of Active Directory and is the domain controller of this Active Directory, I selected `Integrated with Active Directory`. <br>
<imig src="https://github.com/user-attachments/assets/f46e8a16-6ef1-403e-9775-26d394becafa" Width="500" /> <br>
6. The `Remote Installation Folder Location` asks you to select the path / location on a drive that will contain your images. Note that it is best practice (especially in a production environment) to NOT use the same volume that your Windows Server is installed on. For the purpose of this test, I decided to have the path be on the same drive/volume as my Windows Server. <br>
<img src="https://github.com/user-attachments/assets/b531f8cb-c6a4-4b40-8647-845c870c0938" Width="500" />
<img src="https://github.com/user-attachments/assets/1dcc180f-cc7a-4176-b09b-7455434d39e2" Width="500" /> <br>
8. On the `PXE Server Initial Settings` page, choose the most appropriate options. I have chosen `Respond to all client computers (known and unknown)`. <br>
<img src="https://github.com/user-attachments/assets/b0cf640f-4956-4a76-ac17-87e857452f1d" Width="500" /> <br>
9. After, the configuration will be applied and you can either keep the check-box checked to add images to the server now or uncheck the box to do so at a later time and click on `Finish`. <br>
<img src="https://github.com/user-attachments/assets/7a1396ed-a1d4-4440-9c28-65232e8f15aa" Width="500" /> <br>

# Adding Boot and Install Images

Once finished, you will notice several new folders have been created under your selected server. The two primary folders I will be focusing on will be `Install Images` and `Boot Images`. Before anything, make sure to mount your Windows disc file. Simply right click on the Disc Image File and click on `Mount`. This creates a new drive and gives us access to the files inside of the Disc Image. <br>
<img src="https://github.com/user-attachments/assets/c1add14a-00ca-42c1-b373-e313ab173c8a" Width="500" /> <br>

1. Let's work with the `Boot Image` folder first. On the WDS window, fight click on `Boot Image` and click `Add Boot Image`. <br>
<img src="https://github.com/user-attachments/assets/2c66b7f0-bb68-40d0-be65-a10e6594ab7e" Width="500" /> <br>
2. If you known where the boot image file is located, you can type in the directory path for it. Otherwise, click on `Browse` and navigate to where the boot image file is located. This should be in the newly created drive when you mounted the Windows Disc Image earlier within the `Sources` folder. For example, my directory will be `E:\sources` where the E drive is the Disc Image File I mounted earlier. Select `boot.wim` and click `Next`. <br>
<img src="https://github.com/user-attachments/assets/8b6ed472-a2f0-4996-bc13-eaffa3a0e4d6" Width="500" />
<img src="https://github.com/user-attachments/assets/84837eae-d612-40a1-a65a-c42b8b09582d" Width="500" />
<img src="https://github.com/user-attachments/assets/83336081-12cc-4766-8c62-38005d8651c9" Width="500" /> <br>
3. Give the boot image a name and click `Next`. <br>
<img src="https://github.com/user-attachments/assets/92eed5f3-c762-44bf-bb16-98791f1aa9b9" Width="500" /> <br>
4. Review the `Summary` page and click `Next` to add the boot image. <br>
<img src="https://github.com/user-attachments/assets/0a2d7a92-b56a-428a-9342-894dedbfb653" Width="500" /> <br>
5. Right-click on `Install Images` folder in the WDS window and click `Add Install Image`. <br>
<img src="https://github.com/user-attachments/assets/8ac66314-ed97-469c-8379-5f950d5f12a4" Width="500" /> <br>
6. Give the image group a name and click `Next`. <br>
<img src="https://github.com/user-attachments/assets/20589e30-965c-4024-9564-2c65e1a2fe01" Width="500" /> <br>
7. Locate the `install.wim` file like you did when locating the `boot.wim` file (it is in the same directory/location). <br>
<img src="https://github.com/user-attachments/assets/5dfdbb5d-35e9-43f3-9d9a-b57f3597303c" Width="500" /> <br>
8. The `Available Images` page will provide you with a list of available Windows images that can install. Select the ones you want and click `Next`. <br>
<img src="https://github.com/user-attachments/assets/a922019e-5ddd-4016-b28d-fad9f18d8d40" Width="500" /> <br>
9. Review the `Summary` page and click `Next`. <br>
<img src="https://github.com/user-attachments/assets/656cd6b0-1d34-479e-82b1-a1fd6ef39e41" Width="500" /> <br>
10. Once done, you will see a list of available Windows images that can be installed. <br>
<img src="https://github.com/user-attachments/assets/531286be-7d87-47c4-84dc-6f8b7be3ed42" Width="500" /> <br>
