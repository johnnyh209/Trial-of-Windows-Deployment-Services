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
