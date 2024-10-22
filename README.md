<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket - Prerequisites and Installation
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

## Operating Systems Used 

- Windows 10 (21H2)

## List of Prerequisites

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager 
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6

## Installation Steps

1. First, let's create a virtual machine at https://portal.azure.com/. Set up your virtual machine with Windows 10 Pro, version 22H2. Create a virtual machine with at least 2 vcpus and 8GB memory.

2. Once we've created our virtual machine, we will want to connect to it using the public IP address the VM is set up with. We will connect using the remote desktop connection app.

   <img src="https://github.com/user-attachments/assets/3514f7e6-c638-4ae7-adf2-2af58dec25d0" height="40%" width="40%" alt="Public IP Address"/>
  
3. Once connected to our virtual machine we want to go to our control panel. From the control panel let's open up programs. Select, Turn Windows features on and off.

   <img src="https://github.com/user-attachments/assets/490d1e50-885d-49e3-ae03-a81fdebcc78f" height="40%" width="40%" alt="Control Panel"/>
  
   <img src="https://github.com/user-attachments/assets/7081dd84-e4cf-4114-aa94-2c66b9045e5a" height="40%" width="40%" alt="Windows Features"/>
  
4. We will want to install / enable IIS in Windows with CGI and Common HTTP Features
   - World Wide Web Services -> Application Development Features -> 
     - [X] CGI
     - [X] Common HTTP Features
  
   <img src="https://github.com/user-attachments/assets/538170eb-b89a-482f-a21e-490b7627a2f6" height="40%" width="40%" alt="IIS Features"/>
  
   <img src="https://github.com/user-attachments/assets/71ca59f0-119d-4419-ab60-2239ab5f0379" height="40%" width="40%" alt="HTTP Features"/>
  
   ***NOTE*** Make sure all Common HTTP Features are checked.
 
   To make sure the IIS is installed / enabled go to a browser of your choice and search for 127.0.0.1. It will look something like this:
  
   <img src="https://github.com/user-attachments/assets/28ead978-29ae-457c-acfb-abcfb42b4c1e" height="40%" width="40%" alt="Browser 127.0.0.1"/>
  
5. Now that the IIS is enabled, from the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi). Go through the install wizard and complete the install.
  
6. Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
  
7. Create a folder in the C drive called PHP.
  
8. From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP

9. Once we have downloaded and extracted the zip file into the PHP folder on the C drive, download and install the VC_redist.x86.exe from the installation files. Go through the setup wizard to finish setting up and installing the VC_redist.x86.exe. 
  
10. Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi). Run the setup wizard:
    - Typical Setup ->
    - Launch Configuration Wizard (after install) ->
    - Standard Configuration ->

    Make the new root password: Password1
  
    <img src="https://github.com/user-attachments/assets/ec40e5f9-0877-4ba8-82b7-131ca34afd9f" height="40%" width="40%" alt="Root Password"/>
  
    Let's go ahead and execute the process on the next page.
  
    <img src="https://github.com/user-attachments/assets/ce3b510d-0d36-4350-85e7-d85e71c54e74" height="40%" width="40%" alt="Execute"/>
  
11. Now that we have the files downloaded and installed we will want to search for IIS in the Windows search bar. Open IIS as an administrator.

    <img src="https://github.com/user-attachments/assets/8265e6ea-94b8-4903-aff1-4c92e6a47717" height="40%" width="40%" alt="Search IIS"/>
  
    The program should look like this:

    <img src="https://github.com/user-attachments/assets/579616a2-ec72-4b87-bd7a-cd3ffc24c2d0" height="40%" width="40%" alt="IIS Program"/>
  
12. We will now want to register PHP from within IIS.
    - Click on PHP Manager
  
    <img src="https://github.com/user-attachments/assets/f6c54544-731e-4749-8504-b5db4ea28886" height="40%" width="40%" alt="PHP Manager"/>

    - Register new PHP version.
  
    <img src="https://github.com/user-attachments/assets/ebd05e94-39fd-4a48-b97f-85ab5abfea98" height="40%" width="40%" alt="Register New PHP"/>
  
    - We will want to provide a path to the PHP executable file (php-cgi.exe). 
      Go to C Drive -> PHP -> click on php-cgi file.
  
    <img src="https://github.com/user-attachments/assets/62d21913-ac31-4e1d-baa9-c1c453870ea2" height="40%" width="40%" alt="PHP Path"/>
  
    - Restart the IIS server.
  
    <img src="https://github.com/user-attachments/assets/8cb045d6-794c-42cb-9f04-132ed3aa44fd" height="40%" width="40%" alt="Restart IIS Server"/>
  
13. Install osTicket v1.15.8
    - Download osTicket from the Installation Files Folder
    - Extract and copy "upload" folder to c:\inetpub\wwwroot
    - Within c:\inetpub\wwwroot, Rename "upload" to "osTicket"
  
    Reload IIS again.
  
14. On IIS go to sites -> Default -> osTicket
    - On the right, click "Browse *:80"
  
    <img src="https://github.com/user-attachments/assets/95a909f4-4937-46ce-b497-f94f56c173c0" height="40%" width="40%" alt="Browse 80"/>
  
    Some extensions are not enabled on the osTicket browser.
  
    <img src="https://github.com/user-attachments/assets/748a1248-77ce-4148-b489-9fa37ce3740f" height="40%" width="40%" alt="Extensions Disabled"/>
  
    To enable the extensions:
    - Go back to IIS, sites -> Default -> osTicket
    - Double click PHP manager
    - Click "Enable or disable an extension"
  
    <img src="https://github.com/user-attachments/assets/1eefb7fb-e2dd-4dca-b1de-9e29e85897a8" height="40%" width="40%" alt="PHP Manager osTicket"/>
  
    <img src="https://github.com/user-attachments/assets/b91fd619-85d0-478e-a962-3e7d07897f20" height="40%" width="40%" alt="Enable or Disable Extensions"/>
  
    We will want to enable three extensions from here:
    1. php_imap.dll
    2. php_intl.dll 
    3. php_opcache.dll
  
    How to Enable:
  
    <img src="https://github.com/user-attachments/assets/c4450cdc-be8e-47c5-8987-7920bd7b4213" height="40%" width="40%" alt="How To Enable"/>

    All 3 Enabled:

    <img src="https://github.com/user-attachments/assets/753b7fb0-82e9-4fff-9cb3-d2ae46f451e6" height="40%" width="40%" alt="All Enabled"/>
  
  
15. Once we have those extensions enabled in IIS, we are going to want to rename one of the files in our osTicket folder.
    Go into the file explorer and search for C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  
    We are going to rename the ost-sampleconfig.php to ost-config.php
  
    Now that we have renamed the files, right-click on the file and go to properties.
    From there click security, click on advance, and disable the inheritance.
    We will select Remove all inherited permissions from this object.
  
    Now we will add new permissions.
  
    Click Add
  
    <img src="https://github.com/user-attachments/assets/c1c85bb9-aca7-4856-a5c6-833c42272a0c" height="40%" width="40%" alt="Add"/>
  
    Select a principal
  
    <img src="https://github.com/user-attachments/assets/0ae4a225-d149-425f-a379-648334bae993" height="40%" width="40%" alt="Select A Principal"/>
   
    Type "Everyone" in the box. Press "Check Names" and then press OK.
  
    <img src="https://github.com/user-attachments/assets/37aa527d-ec76-47d5-9ef7-b1c4931ac725" height="40%" width="40%" alt="Everyone"/>
  
    Let's make sure Full Control and all the other boxes are checked.
  
    <img src="https://github.com/user-attachments/assets/e354123b-1f34-46dc-a2cb-4693a3b63e17" height="40%" width="40%" alt="Full Control"/>
  
    Click Apply and Ok.
  
    <img src="https://github.com/user-attachments/assets/3499101d-b0e2-42f6-8b87-b7fb03045bd4" height="40%" width="40%" alt="Disk Sanitization Steps"/>
  
    Once that is done we will continue to setup osTicket in the browser. Click Continue on the osTicket browser page.
    Fill out the page as required except for the Database Settings at the bottom of the page. We will get to that. 
  
    We will want to download and install HeidiSQL from the Installation Files. 
  
    <img src="https://github.com/user-attachments/assets/8ba845b3-048d-4c05-b9ff-c9cd2a4d4546" height="40%" width="40%" alt="Heidi Install"/>
  
    When the program is open we will create a new session in it.
  
    <img src="https://github.com/user-attachments/assets/8256ef39-5b1e-4729-9dd7-edd63b79036a" height="40%" width="40%" alt="New Session"/>
  
    We want to make sure the username is "root" and the password is "Password1".
  
    <img src="https://github.com/user-attachments/assets/26a59a4f-a394-4420-8a2b-d05be50b2c60" height="40%" width="40%" alt="Username and Password"/>
 
    We will now create a new database within HeidiSQL. In Heidi right click on the left side where it says "Unnamed", select "create new", and then select "database".
  
    <img src="https://github.com/user-attachments/assets/b08f3e07-ae5e-40f7-bf53-6e97ff24c80f" height="40%" width="40%" alt="New Database"/>
    
    Name the new database osTicket.
    
    <img src="https://github.com/user-attachments/assets/f154845b-9344-413e-ae9f-d54729d19b4f" height="40%" width="40%" alt="Name osTicket"/>
    
    Under the Database Settings in the browser, the username will be root and the password will be Password1. For MySQL Database type in osTicket.
  
    <img src="https://github.com/user-attachments/assets/bcd48aff-34e3-4713-a707-0304212f76ad" height="40%" width="40%" alt="Database osTicket"/>
  
    The last step is to do some cleanup. We will want to delete the setup folder in our system. 
    - Delete: C:\inetpub\wwwroot\osTicket\setup
    Only delete the setup folder and nothing else.
  
    We then will want to set the permissions back to "Read" only in the ost-config.php file.
  
    <img src="https://github.com/user-attachments/assets/db653184-58c5-439f-b516-42acc24f25b6" height="40%" width="40%" alt="Read Only"/>
  
    <img src="https://github.com/user-attachments/assets/8161512a-978b-4eb6-9e92-9688439b7a9c" height="40%" width="40%" alt="Permissions"/>
  
    The last step after that is to log in to osTicket on the browser at http://localhost/osTicket/scp/login.php
  
    <img src="https://github.com/user-attachments/assets/e7a6fe02-2937-4094-80cb-3cb1967256fd" height="40%" width="40%" alt="Log in"/>
  
Congrats! You have now successfully installed and set up osTicket!
