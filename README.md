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
<p>Create an Azure Virtual Machine Windows 10, 4 vCPUs</p>
<p>⦁	Name: osticket-vm</p>
<p>⦁	Username: labuser</p>
<p>⦁	Password: osTicketPassword1!</p>

<p>Log into the VM with Remote Desktop</p>

Within the VM (osticket-vm), download the osTicket-Installation-Files.zip and unzip it onto your desktop. The folder should be called “osTicket-Installation-Files”

⦁	We will use the files in this folder to install osTicket and some of the dependencies.
![Capture](https://github.com/user-attachments/assets/382ed086-7bcb-4df0-b5f6-5a49c50d01ee)
<p>All this files could be found on osTicket website.</p>

<h2>Installation Steps</h2>

Install / Enable IIS in Windows WITH CGI
⦁	World Wide Web Services -> Application Development Features -> [X] CGI
![Capture2](https://github.com/user-attachments/assets/f53a80b4-5332-489b-b067-9639fd8c0870)
![Capture3](https://github.com/user-attachments/assets/13b4e3e0-451c-44ca-a407-35f4f9bcb5b7)
![Capture4](https://github.com/user-attachments/assets/a94c7284-bace-4ba1-b632-a832798c7d40)

<p>From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)</p>

<p>From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)</p>

<p>Create the directory C:\PHP</p>

From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
![Capture5](https://github.com/user-attachments/assets/c7609496-921a-46b1-af4f-222dc157c88f)

From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.

From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
<p>⦁	Typical Setup -></p>
<p>⦁	Launch Configuration Wizard (after install) -></p>
<p>⦁	Standard Configuration -></p>
<p>⦁	Username: root</p>
<p>⦁	Password: root</p>

Open IIS as an Admin
![Capture6](https://github.com/user-attachments/assets/2d8d7ade-4bd6-40d8-8d03-b5fd6eca5433)

Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)
![Capture7](https://github.com/user-attachments/assets/b2a409af-4c46-4959-b294-7eb6b84f3715)

Reload IIS (Open IIS, Stop and Start the server)

Install osTicket v1.15.8
<p>⦁	From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”</p>
<p>⦁	Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”</p>

![Capture8](https://github.com/user-attachments/assets/afb379ca-cfd4-45ee-ac7f-b86edb15c0bd)

Reload IIS (Open IIS, Stop and Start the server)

<p>In IIS go to sites -> Default -> osTicket</p>
<p>⦁	On the right, click “Browse *:80”</p>

![Capture9](https://github.com/user-attachments/assets/f5e54868-62c1-4464-9a37-8d8c93ec5fe1)
![Capture10](https://github.com/user-attachments/assets/afbf2dfe-065a-4674-8589-8ebe52f904b4)

Note that some extensions are not enabled
<p>⦁	Go back to IIS, sites -> Default -> osTicket</p>
<p>⦁	Double-click PHP Manager</p>
<p>⦁	Click “Enable or disable an extension”</p>
  <p>  ⦁	Enable: php_imap.dll</p>
  <p>  ⦁	Enable: php_intl.dll</p>
  <p>  ⦁	Enable: php_opcache.dll</p>

![Capture11](https://github.com/user-attachments/assets/382d4b18-80fb-4166-b852-a6ce06a97392)
![Capture12](https://github.com/user-attachments/assets/39713c8a-b555-4d47-bf85-955c7bc7e325)

<p>⦁	Refresh the osTicket site in your browser, observe the changes</p>

<p>Rename: ost-config.php</p>
<p>⦁	From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php</p>
<p>⦁	To: C:\inetpub\wwwroot\osTicket\include\ost-config.php</p>

![Capture13](https://github.com/user-attachments/assets/8b5be919-9079-49f3-aa67-8a7293ccc182)

<p>Assign Permissions: ost-config.php</p>
<p>⦁	Disable inheritance -> Remove All</p>
<p>⦁	New Permissions -> Add  -> Everyone -> All (Full  control)</p>

![Capture14](https://github.com/user-attachments/assets/be5bbea7-d578-4ed2-9bd1-4c03d22e9ee2)
![Capture15](https://github.com/user-attachments/assets/c4b2b116-e065-440c-aced-ec8cad937559)
![Capture16](https://github.com/user-attachments/assets/b0a674b2-1d44-4a79-9000-c6f8f8478358)

<p>Continue Setting up osTicket in the browser (click Continue)</p>
<p>⦁	Name Helpdesk</p>
<p>⦁	Default email (receives email from customers)</p>

![Capture17](https://github.com/user-attachments/assets/b735857d-8c0e-4fd2-9613-570fa7059065)
![Capture17 5](https://github.com/user-attachments/assets/5f7fa1cd-eeb7-4f9f-b092-0fa12303c081)

<p>From the “osTicket-Installation-Files” folder, install HeidiSQL.</p>
<p>⦁	Open Heidi SQL</p>
<p>⦁	Create a new session, root/root</p>
<p>⦁	Connect to the session</p>
<p>⦁	Create a database called “osTicket” Righ-click Unnamed-> Create new -> Database</p>

![Capture18](https://github.com/user-attachments/assets/554a7230-8a38-4b01-a110-4af70f4e1c2c)
![Capture19](https://github.com/user-attachments/assets/dbfc8dfa-114f-4396-9388-65bde4a4639e)

<p>Continue Setting up osTicket in the browser</p>
<p>⦁	MySQL Database: osTicket</p>
<p>⦁	MySQL Username: root</p>
<p>⦁	MySQL Password: root</p>
<p>⦁	Click “Install Now!”</p>

![Capture20](https://github.com/user-attachments/assets/9f380ee7-0856-43c5-bad8-0c7ec71aa04d)
![Capture21](https://github.com/user-attachments/assets/a920b6de-c2f9-4475-8478-79e494258cef)

<p>Congratulations, hopefully it is installed with no errors!</p>
 <p>⦁	Browse to your help desk login page:</p>
 <p>http://localhost/osTicket/scp/login.php</p>
 
<p>End Users osTicket URL:</p>
<p>⦁	http://localhost/osTicket/ </p>



