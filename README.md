<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket guide - Post Installation Setup (Part 1 of 3)</h1>
This guide outlines the prerequisites and installation of the help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Create an Azure Virtual Machine Windows 10, 4 vCPUs
    https://portal.azure.com/
    Microsoft Azure Documentation: https://learn.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal
    Name: Vm-osticket
    Username: labuser (your choice)
    Password: osTicketPassword1! (your choice)
    
- Install / Enable IIS in Windows WITH CGI
  - World Wide Web Services -> Application Development Features -> [X] CGI
  - Download and install PHP Manager for IIS https://www.iis.net/downloads/community/2018/05/php-manager-150-for-iis-10
  - Download and install Rewrite Module https://www.iis.net/downloads/microsoft/url-rewrite
  - Create a new directory(file folder) in the root(main parent folder) of the drive where windows is installed, usually "C:\" and
    call it "PHP"
    -Do so by opening the root windows folder with windows explorer, right clicking in the open space below the folders, hover over "new",
     click "folder".
  - Download PHP 7 3.8 https://www.php.net/downloads.php & unzip downloaded folder to the new directory.
    -In Edge, make sure to click "keep" -> Show More -> Keep anyway to download the zip file. 
    -Inside the downloads folder within windows explorer, right click the zip folder, click "extract all", and browse to the 
     new folder you created called PHP. Make sure this last folder called PHP is selected before you extract.
  - Download and install VC_redist.x86.exe https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170
  - Doanload and install MySQL 5.5.62 https://downloads.mysql.com/archives/community/
  - Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration -> Password1
  - Open IIS as an Admin
  - Register PHP from within IIS
  - Reload IIS (Open IIS, Stop and Start the server)
  - Install osTicket v1.15.8
      Download osTicket-v1.15.8.zip from github
      Extract and copy “upload” folder to c:\inetpub\wwwroot
      Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
  - Reload IIS (Open IIS, Stop and Start the server)
  - Go to sites -> Default -> osTicket
    -On the right, click “Browse *:80”
  - Some extensions are not enabled and need to be
    -Go back to IIS, sites -> Default -> osTicket
    -Double-click PHP Manager
    -Click “Enable or disable an extension”
    -Enable: php_imap.dll
    -Enable: php_intl.dll
    -Enable: php_opcache.dll
    -Refresh the osTicket site in your browse, observe the changes
  - Rename: ost-config.php
     From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
     To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
  - Assign Permissions: ost-config.php
  - Disable inheritance -> Remove All
  - New Permissions -> Everyone -> All
  - Continue Setting up osTicket in the browser (click Continue)
     Name Helpdesk
     Default email (receives email from customers)
  - Download & Install HeidiSQL https://www.heidisql.com/download.php
     Open Heidi SQL
     Create a new session, root/Password1
     Connect to the session
     Create a database called “osTicket”
  - Continue Setting up osticket in the browser
     MySQL Database: osTicket
     MySQL Username: root
     MySQL Password: Password1
     Click “Install Now!”
  - Browse to your help desk login page: http://localhost/osTicket/scp/login.php  
  - End Users osTicket URL: http://localhost/osTicket/ 

<a href="https://github.com/zdadams1/post-install-config/edit/main/README.md">Post Installation Setup Guide</a>

