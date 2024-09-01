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

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- PHP Manager For IIS
- Rewrite_amd64_en-US.msi
- php-7.3.8-nts-Win32-VC15-x86.zip
- VC_redist.x86.exe
- My SQL 5.5.62
- OS Ticket v1.15.8
- HeidiSQL
- Installation Files (https://drive.google.com/drive/folders/1h9A9xpidPwQy1-mtO9f05FAAVb9bvD1U?usp=share_link) <h2>Installation Steps</h2>

<img width="1767" alt="Screen Shot 2024-05-19 at 9 08 59 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/35d881bb-b0d7-4969-a021-d7b583ec2343">

Step 1. Create a Resource Group in Azure 

  
<img width="1078" alt="Screen Shot 2024-05-19 at 9 11 36 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/472a4d2f-9633-4839-bff1-92fe174f459e">

Step 2. Create a Windows 10 pro Virtual Machine (VM) with 2-4 Virtual CPUs
  -  Name: VM-osTicket
  - Username: labuser (or what ever you decide to choose for a username)
  - Password: osTicketPassword1!(example)
  - When creating the VM, Create a new Virtual Network (Vnet) 
  - Click Review+Create

  
<img width="1849" alt="Screen Shot 2024-05-19 at 9 16 44 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/dc073a69-65c0-41f4-87ab-fdfb053814b6">

Step 3. Open Microsoft Remote Desktop (If on Mac Desktop)
  - Click Add PC and enter your VMs public IP (Wait until the VM finishes deploying) 
  - Enter the username and password you put in for your VM


<img width="1214" alt="Screen Shot 2024-05-19 at 9 36 44 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/ca4884b9-8dfb-4198-a555-f2368427475d">

Step 4: Install/Enable IIS in Windows with CGI and Common HTTP features 
- right click on the "start" icon, Click run, and enter "control"
- Click on "programs" and then "turn windows features on or off"
- clikc on internet information services -> World Wide Web Services -> Application Development Features ->
[X] CGI
[X] Common HTTP Features
- Internet Information Services -> Web Management Tools -> IIS Management Console
	[X] IIS Management Console
- Click Ok

<img width="1532" alt="Screen Shot 2024-05-19 at 10 11 10 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/f752a179-4c8d-4696-9977-e19c824f6054">
  
Step 5. Open the Installation files page here:
(https://drive.google.com/drive/folders/1h9A9xpidPwQy1-mtO9f05FAAVb9bvD1U?usp=share_link) 
- Download and isntall PHP Manager for IIS
- Download and install Rewrite Module
- Download and install PHP 7.3.8
- Download and install VC_redist.x86.exe.
- Download and install MySQL 5.5.62
  When MySQL downloads: Typical setup -> Launch Configuration Wizard(after install) -> Standard Configuration -> Password1 -> Execute 
  
Note: if you dont see anything happen immediately after clicking download, give it a few seconds. 


<img width="1332" alt="Screen Shot 2024-05-19 at 10 04 33 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/8a72fa53-8fbf-4840-bdc3-1ed62d68511f">

When PHP 7.3.8 is finished downloading, Create a folder "PHP" on Windows (C:). right click the PHP 7.3.8 file -> extract all -> browse -> This PC -> Windows (C:) -> PHP -> Select Folder -> Extract

<img width="1137" alt="Screen Shot 2024-05-19 at 10 24 24 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/8f600f98-ee68-4419-aa7f-0ea2384d0d0b">

Step 6. Open IIS as an Admin
- on the search bar type IIS -> right click on IIS and click "run as administrator"
- Register PHP from within IIS
- Click on PHP Manager -> Register new PHP version -> "..." -> this PC -> PHP -> php-cgi -> open
- Go back to the home page and click "Restart"

<img width="823" alt="Screen Shot 2024-05-19 at 10 32 17 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/89c39bc9-7e69-4187-967f-1a15fd8ef549">

Step 7. Download and Install osTicket v1.15.8
- When downloaded, open the osTicket file
- once inside the folder, open another file explorer and go to This PC -> Windows (C:) -> inetpub -> wwwroot
- On the wwwroot folder, drag the "upload" folder to the "wwwroot" folder
- Rename the "upload" folder to "osTicket


<img width="1533" alt="Screen Shot 2024-05-19 at 10 37 17 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/90384f4f-d932-4134-873b-72fac36da6c9">

Step 8. Go back to IIS Manager
- Click restart
- Go to sites -> Default -> osTicket
- On the right, click "Browse *:80"
- When click on that, you should see it opening the webpage shown on the image.

Note: if you dont see this and instead an error page, something was done wrong. 

<img width="909" alt="Screen Shot 2024-05-19 at 10 44 42 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/55ab8449-d9e2-4d8f-9a8a-d026fe10278d">

Step 9. Some extensions are not enabled. 
- Go back to IIS -> sites -> Default -> osTicket
- Double click PHP Manager
- Click "Enable or Disable an extension"
   Enable: php_imap.dll
   Enable: php_intl.dll
   Enable: php_opcache.dll
  

<img width="1683" alt="Screen Shot 2024-05-19 at 10 45 01 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/7153ee4b-9d13-4e17-ab82-b3af48a36d0f">
  
Refresh the osTicket site in your browser, observe the changes




<img width="798" alt="Screen Shot 2024-05-19 at 10 50 39 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/09c14a6d-8af3-48a6-9e39-2939718dd12b">

Step 10. Rename: ost-config.php
 - Go to the wwwroot folder
 - click on osTicket -> include
 - look for the file "ost-sampleconfig.php and rename it to "ost-config.php"
 - Right click ost-config.php -> Properties -> Security -> Advance -> Disable inheritance -> Remove all -> Add -> Select Principle -> type "Everyone" -> Ok -> click "Full Controll" -> ok -> Apply and then OK


<img width="693" alt="Screen Shot 2024-05-19 at 11 05 09 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/1b9810b8-dd89-4864-ade0-7174ee03ab63">

Step 11. Download and Install HeidiSQL
 - Open HeidiSQL
 - Create a new session, root/Password1
 - Connect to the session
 - Create a database called "osTicket"


<img width="1685" alt="Screen Shot 2024-05-19 at 11 07 01 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/20749194-2394-4e34-85da-8c9b8f0cbee7">
 
Step 11. Continue Setting up Osticket in the browser
 - Name HelpDesk
 - Derek@helper.com (receives email from customers)
 - MySQL Database: osTicket
 - MySQL Username: root
 - MySQL Password: Password1
 - Click "Install Now!"

<img width="1684" alt="Screen Shot 2024-05-19 at 11 11 41 AM" src="https://github.com/DereHz/osTicket-prereqs/assets/169094076/8cef074d-347a-4aa8-9964-755133a3ba63">

"Congratulations"



Clean up 
 - Delete: C:\inetpub\wwwroot\osTicket\setup
 - Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php




