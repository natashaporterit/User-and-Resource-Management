# User-and-Resource-Management

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Enable Internet Information Services (IIS)
- Install Web Platform Installer
- Install MySQL & Set up a Username & Password
- Install C++ Redistributable
- Configure Permissions & Install OS Ticket

<h2>Installation Steps</h2>

<p>
<img width="493" height="460" alt="image" src="https://github.com/user-attachments/assets/06028eb6-8afe-4265-9fa3-f476b78eba18" />

</p>
<p>
To install the Support Ticket System, start by creating an Azure subscription and setting up a resource group to organize related resources. Next, configure a virtual network and define a subnet within it to manage network traffic. Once the network is ready, deploy a virtual machine (VM) inside the subnet. Finally, install the required prerequisites and then set up the Support Ticket System on the VM. 
  
If you would like to speed up this process, you can go straight to creating the virtual machine and set up the virtual network and subnet as part of the settings for the virtual machine. 
</p>
<br />

<p>
<img width="408" height="401" alt="image" src="https://github.com/user-attachments/assets/db7b1534-bc92-485f-8740-8a9c2fce2ebd" />
</p>
<p>
To enable Internet Information Services (IIS), log into the virtual machine, access the control panel, and click on the option titled "Turn Windows Features On or Off." Another window will pop up that allows you to mark the box to TURN ON INTERNET INFORMATION SERVICES. For this feature to work properly, you will also have to expand the following options: IIS, WORLD WIDE WEB SERVICES, application development features and then mark the box for CGI. Then press ok. This will install the web server.
</p>
<br />

<p>
<img width="1115" height="629" alt="image" src="https://github.com/user-attachments/assets/df0c2cf9-7f64-49c4-9c3b-ed0abe109bac" />
</p>
<p>
Install PHP Manager for IIS from the “osTicket-Installation-Files” folder, </p>
<br />

<p>
<img width="1110" height="623" alt="image" src="https://github.com/user-attachments/assets/1e822d7f-ea35-41e2-a9be-dbff282fa9ba" />
</p>
<p>
From the “osTicket-Installation-Files” folder, install the Rewrite Module
</p>
<br />

<p>
<img width="1120" height="698" alt="image" src="https://github.com/user-attachments/assets/358a9af5-3e40-48c8-8c9c-9fda502929fd" />
</p>
<p>
Create the directory C:\PHP

From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
</p>
<br />

<p>
<img width="1066" height="622" alt="image" src="https://github.com/user-attachments/assets/ae54f250-1690-47da-ab0f-c79def2c9553" />
</p>
<p>
From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe
</p>
<br />

<p>
<img width="1072" height="614" alt="image" src="https://github.com/user-attachments/assets/f6a6e671-aede-4ba0-ad3f-45fdd505f926" />
</p>
<p>
From the “osTicket-Installation-Files” folder, install MYSQL 5.5.62. When given the option select "standard" setting.
</p>
<br />

<p>
<img width="1112" height="626" alt="image" src="https://github.com/user-attachments/assets/a7ea55f0-034f-4911-902f-36d8ce4ec134" />
</p>
<p>
Create a password for the "Modify Security Settings" option. And finish setup for MySQL
</p>
<br />

<p>
<img width="1444" height="848" alt="image" src="https://github.com/user-attachments/assets/56592da9-e350-4959-b40e-1fa223c25aa3" />
</p>
<p>
Open IIS as an Admin by searching for it in the search bar, then right-click to find the option to "run as admin." We will register PHP within IIS by clicking on PHP Manager, Register New PHP Version, click the three dots to brows to the folder on the C drive labeled PHP, click on the executable and press okay.
</p>
<br />

<p>
<img width="1116" height="633" alt="image" src="https://github.com/user-attachments/assets/3f4a06a1-64d9-4596-b2f4-8e14dc235158" />
</p>
<p>
Reload IIS server. From the “osTicket-Installation-Files” folder, extract the “osTicket-v1.15.8.zip” contents and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, rename “upload” to “osTicket.” Reload IIS.

</p>
<br />

<p>
<img width="920" height="875" alt="image" src="https://github.com/user-attachments/assets/e4e185f7-2c14-44e3-9ed0-336b8527e2ca" />
</p>
<p>
To access the osTicket site, go to Sites → Default → osTicket in IIS, then click *“Browse :80” on the right side to open it in your browser. If you see a message indicating that some PHP extensions are not enabled, return to IIS and open PHP Manager under the same osTicket site. Next, select “Enable or disable an extension.” From the list, enable the following extensions: php_imap.dll, php_intl.dll, and php_opcache.dll. After enabling them, refresh the osTicket site in your browser and observe the updated changes.
</p>
<br />

<p>
<img width="554" height="827" alt="image" src="https://github.com/user-attachments/assets/d5227804-621e-4eb0-a4b2-e74b7c86ae81" />
</p>
<p>
Next, you’ll need to rename one of the osTicket files. Go to C:\inetpub\wwwroot\osTicket\include, find the file named ost-sampleconfig.php, and rename it to ost-config.php. Once that’s done, right-click the file, open Properties → Security, and adjust the permissions. Disable inheritance, remove all existing permissions, then add a new one for Everyone and give it Full Control.

Now, head back to your browser to continue setting up osTicket. Click Continue, give your helpdesk a name, and enter the default email address that will receive messages from customers.

Next, you’ll set up the database. Open your osTicket-Installation-Files folder and install HeidiSQL. Once installed, open it and create a new session using the credentials root for both the username and password. Connect to that session, then create a new database named osTicket.

Finally, go back to your browser to finish the setup. When prompted, enter the following details:

MySQL Database: osTicket

MySQL Username: root

MySQL Password: root

Once everything looks good, click Install Now! and your osTicket setup will be complete.
</p>
<br />

<img width="548" height="425" alt="image" src="https://github.com/user-attachments/assets/8b0e2838-c429-489a-ad0c-a6ebb2c72d66" />

