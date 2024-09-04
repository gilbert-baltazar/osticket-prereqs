# osTicket-prereqs
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

<h2>List of Prerequisites</h2>

- PHP Manager For IIS
- Rewrite_amd64_en-US.msi
- php-7.3.8-nts-Win32-VC15-x86.zip
- VC_redist.x86.exe
- My SQL 5.5.62
- OS Ticket v1.15.8
- HeidiSQL
- Installation Files (https://drive.google.com/drive/folders/1h9A9xpidPwQy1-mtO9f05FAAVb9bvD1U?usp=share_link) <h2>Installation Steps</h2>

![Screenshot 2024-09-02 at 8 47 41 PM](https://github.com/user-attachments/assets/9e595ae7-a75d-4fd2-a85a-53f5ad6ac464)

Step 1. Create a Resource Group in Azure 
  
![Screenshot 2024-09-02 at 8 50 14 PM](https://github.com/user-attachments/assets/592127c7-cf2c-41d8-bcaa-e2a4f260ef77)

Step 2. Create a Windows 10 pro Virtual Machine (VM) with 2-4 Virtual CPUs
  -  Name: VM-osTicket
  - Username: labuser (or what ever you decide to choose for a username)
  - Password: osTicketPassword1!(example)
  - When creating the VM, Create a new Virtual Network (Vnet) 
  - Click Review+Create

  
![Screenshot 2024-09-03 at 5 39 49 PM](https://github.com/user-attachments/assets/83efd003-d1b0-4991-93f5-641bc8c2264a)

Step 3. Open Microsoft Remote Desktop (If on Mac Desktop)
  - Click Add PC and enter your VMs public IP (Wait until the VM finishes deploying) 
  - Enter the username and password you put in for your VM


![Screenshot 2024-09-03 at 5 53 12 PM](https://github.com/user-attachments/assets/ea342963-3016-4c75-994a-4450cda04877)

Step 4: Install/Enable IIS in Windows with CGI and Common HTTP features 
- right click on the "start" icon, Click run, and enter "control"
- Click on "programs" and then "turn windows features on or off"
- clikc on internet information services -> World Wide Web Services -> Application Development Features ->
[X] CGI
[X] Common HTTP Features
- Internet Information Services -> Web Management Tools -> IIS Management Console
	[X] IIS Management Console
- Click Ok

![Screenshot 2024-09-03 at 6 01 56 PM](https://github.com/user-attachments/assets/1bd04e3a-fe78-4c2d-9645-4dc8287c8ddc)
  
Step 5. Open the Installation files page here:
(https://drive.google.com/drive/folders/1h9A9xpidPwQy1-mtO9f05FAAVb9bvD1U?usp=share_link) 
- Download and isntall PHP Manager for IIS
- Download and install Rewrite Module
- Download and install PHP 7.3.8
- Download and install VC_redist.x86.exe.
- Download and install MySQL 5.5.62
  When MySQL downloads: Typical setup -> Launch Configuration Wizard(after install) -> Standard Configuration -> Password1 -> Execute 
  
Note: if you dont see anything happen immediately after clicking download, give it a few seconds. 


![Screenshot 2024-09-03 at 6 16 46 PM](https://github.com/user-attachments/assets/95deeb76-10a8-4fd5-b17c-fb3aedc19f66)

When PHP 7.3.8 is finished downloading, Create a folder "PHP" on Windows (C:). right click the PHP 7.3.8 file -> extract all -> browse -> This PC -> Windows (C:) -> PHP -> Select Folder -> Extract

![Screenshot 2024-09-03 at 6 25 10 PM](https://github.com/user-attachments/assets/23955c8b-b07e-4aa0-af19-51915a2164e0)

Step 6. Open IIS as an Admin
- on the search bar type IIS -> right click on IIS and click "run as administrator"
- Register PHP from within IIS
- Click on PHP Manager -> Register new PHP version -> "..." -> this PC -> PHP -> php-cgi -> open
- Go back to the home page and click "Restart"

![Screenshot 2024-09-03 at 6 35 04 PM](https://github.com/user-attachments/assets/b7ce868e-b324-4753-a048-1f8572ff04f2)

Step 7. Download and Install osTicket v1.15.8
- When downloaded, open the osTicket file
- once inside the folder, open another file explorer and go to This PC -> Windows (C:) -> inetpub -> wwwroot
- On the wwwroot folder, drag the "upload" folder to the "wwwroot" folder
- Rename the "upload" folder to "osTicket


![Screenshot 2024-09-03 at 6 36 10 PM](https://github.com/user-attachments/assets/76786c00-0296-414d-ba05-a1adaf3e9416)

Step 8. Go back to IIS Manager
- Click restart
- Go to sites -> Default -> osTicket
- On the right, click "Browse *:80"
- When click on that, you should see it opening the webpage shown on the image.

Note: if you dont see this and instead an error page, something was done wrong. 

![Screenshot 2024-09-03 at 6 39 43 PM](https://github.com/user-attachments/assets/b7e60e43-aef2-4140-b8bb-266e9b7a63ea)

Step 9. Some extensions are not enabled. 
- Go back to IIS -> sites -> Default -> osTicket
- Double click PHP Manager
- Click "Enable or Disable an extension"
   Enable: php_imap.dll
   Enable: php_intl.dll
   Enable: php_opcache.dll
  

![Screenshot 2024-09-03 at 6 49 57 PM](https://github.com/user-attachments/assets/cfdd800e-086c-48a5-bd79-ccef835cb959)
  
Refresh the osTicket site in your browser, observe the changes




![Screenshot 2024-09-03 at 6 51 20 PM](https://github.com/user-attachments/assets/10f54581-468e-4596-a732-e385996f80ff)

Step 10. Rename: ost-config.php
 - Go to the wwwroot folder
 - click on osTicket -> include
 - look for the file "ost-sampleconfig.php and rename it to "ost-config.php"
 - Right click ost-config.php -> Properties -> Security -> Advance -> Disable inheritance -> Remove all -> Add -> Select Principle -> type "Everyone" -> Ok -> click "Full Controll" -> ok -> Apply and then OK


![Screenshot 2024-09-03 at 7 04 31 PM](https://github.com/user-attachments/assets/5da075f8-33f4-4899-bff9-216864b000f6)

Step 11. Download and Install HeidiSQL
 - Open HeidiSQL
 - Create a new session, root/Password1
 - Connect to the session
 - Create a database called "osTicket"

![Screenshot 2024-09-03 at 7 06 52 PM](https://github.com/user-attachments/assets/014c7c2e-295d-49fc-a1d8-b3f3747b8cd1)

Step 11. Continue Setting up Osticket in the browser
 - Name HelpDesk
 - johndoek@helper.com (receives email from customers)
 - MySQL Database: osTicket
 - MySQL Username: root
 - MySQL Password: Password1
 - Click "Install Now!"

![Screenshot 2024-09-03 at 7 10 54 PM](https://github.com/user-attachments/assets/18790fe4-e6ef-4a15-93f5-715c8cbe0acb)

"Congratulations"



Clean up 
 - Delete: C:\inetpub\wwwroot\osTicket\setup
 - Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php




