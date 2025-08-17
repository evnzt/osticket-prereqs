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

- Install and configure IIS with CGI
- Install and configure PHP
- Install and configure MySQL / HeidiSQL
- Download and set up osTicket
- Configure osTicket in the web browser
- Finalize the setup and secure the system

<h2>Installation Steps</h2>

<p>
<img width="415" height="599" alt="image" src="https://github.com/user-attachments/assets/e813a8f7-ce3d-4f64-8d8b-8ab916872183" />
</p>
<p>
  
  __Step 1__: Install and Configure Internet Information Services (IIS) with Common Gateway Interface (CGI) to create a web server:
  - Press Windows key + R for the Direct Run command
  - Type: $\color{#d97706}{\text{optionalfeatures}}$
  - Check ✔ **_"Internet Information Services"_** box
  - Expand **_"Internet Information Services"_** by clicking the + sign
  - Expand **_"World Wide Web Services"_**
  - Expand **_"Application Development Features"_**
  - Check ✔ **_"CGI"_** → click **_"OK"_** → when installation is complete click **_"Close"_**
  - Type $\color{#d97706}{\text{127.0.0.1}}$ in web browser to see the default IIS web page → If done correctly, you should see the default IIS web page
<img width="1106" height="524" alt="image" src="https://github.com/user-attachments/assets/cafccc8c-8ea4-4030-81b9-13aa2d9923ff" />
</p>
<br />
<p>
  
  __Step 2__: Download and Install PHP:
  - Go to ➤ https://github.com/RonaldCarter/PHPManager/releases/tag/V1.5.0
  - Download and install __"PHPManagerForIIS_V1.5.0.msi"__ - _PHPManager_
  - Go to ➤ https://www.iis.net/downloads/microsoft/url-rewrite
  - Download and install __"x86 installer"__ - _Rewrite Module_
  - Go to ➤ https://windows.php.net/downloads/releases/archives
  - Download __"php-7.3.8-nts-Win32-VC15-x86.zip"__ - _PHP Builds_
  - Create the directory: $\color{#d97706}{\text{"C:\PHP"}}$
  - Extract the downloaded PHP Build to: $\color{#d97706}{\text{"C:\PHP"}}$
  - Go to ➤ https://www.microsoft.com/en-us/download/details.aspx?id=48145
  - Download and install __"VC_redist.x86.exe"__ - _Visual C++ Redistributable_
</p>
<br />
<p>
  
  __Step 3__: Install and Configure MySQL:
  - Go to ➤ https://www.npackd.org/p/com.mysql.MySQLCommunityServer/5.5.62
  - Download __"mysql-5.5.62-win32.msi"__
  - Go to ➤ https://www.heidisql.com/installers/HeidiSQL_12.3.0.6589_Setup.exe
  - Download __"HeidiSQL_12.3.0.6589_Setup.exe"__
  - Install MySQL
  - Select the following options:
  > Setup Type – _Typical_ → _Next_  
  > Action Button - _Install_  
  > User Account Control Prompt - _Yes_  
  > Dialog Box (after install) – _Launch the MySQL Instance Cofiguration Wizard_  
  > Action Button - _Finish_  
  > User Account Control Prompt - _Yes_  
  > MySQL Server Instance Cofiguration Wizard - _Next_  
  > Configuration Type – _Standard Configuration_ → _Next_  
  > Windows Option – _Install As Windows Service_ → _Launch the MySQL Server automatically_ → _Next_  
  > Security Options - _Modify Security Settings Dialog Box_ → _Set a root password_ → _Next_  
  > Action Buttons - _Execute_ → _Finish_
  - Install MySQL & HeidiSQL
  - Select the following options:
  > License Agreement – _I accept the agreement_ → _Next_  
  > Select Destination Location – _Next_  
  > Select Start Menu Folder – _Next_  
  > Select Additional Tasks – _Next_  
  > Ready to Install – _Install_  
  > Dialog Box (after install) – _Launch HeidiSQL_  
  > Action Button - _Finish_  
  > Check for HeidiSQL updates - _Skip_  
  > HeidiSQL Session Manager - _New_ → _Open_
  - Connect to the HeidiSQL session
  - Right-Click the **_"Session Name"_** on the left panel of the HeidiSQL Session Manager → Create New → Database
  - Name the newly created database **_"osTicket"_** → _OK_
</p>
<br />
<p>
  
  __Step 4__: Register and Configure PHP from within IIS:
  - Open IIS Manager as Admin
  - Double-click PHP Manager
  - Select: _Register new PHP version_
  - Provide a path to the php executable file: $\color{#d97706}{\text{"C:\PHP\php-cgi.exe"}}$
  - Reload IIS (__Right click__ server, __Stop__ and then __Start__)
</p>
<br />
<p>
  
  __Step Step 5__: Download and Install osTicket:
  - Go to ➤ https://osticket.com/download
  - Download the latest stable release (_.zip file_)
  - Extract the **_"upload"_** folder from **_"osTicket"_** folder to: $\color{#d97706}{\text{"C:\inetpub\wwwroot"}}$
  - Rename the newly extracted **_"upload"_** folder within $\color{#d97706}{\text{"C:\inetpub\wwwroot"}}$ to **_"osTicket"_**
  - Reload IIS (__Right click__ server, __Stop__ and __then Start__)
  - Expand the osTicket server under **_"Connections"_** on the left panel of the IIS Manager
  - Next expand **_"Server"_** → **_"Sites"_** → **_"Default Web Site"_**
  - Select the **_"osTicket"_** folder
  - Click on **_"Browse *:80"_** under **_"Actions"_** on the right panel of the IIS Manager
  - If done correctly, you should see the osTicket installer web page
  - Note that some extensions are not enabled
  - Go back to IIS → **_"Server"_** → **_"Sites"_** → **_"Default Web Site"_** → **_"osTicket"_**
  - Double-click PHP Manager
  - Click **_“Enable or disable an extension”_** under **_"PHP Extensions"_** & enable the following PHP extensions:
  > php_imap.dll  
  > php_intl.dll  
  > php_intl.dll
  - Refresh the osTicket site in your browser, and observe the changes
</p>
<br />
<p>
  
 __Step 6__: Configure **_”ost-config”_**:
  - Rename **_”ost-config”_** from: $\color{#d97706}{\text{"C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php"}}$
  - Rename to: $\color{#d97706}{\text{"C:\inetpub\wwwroot\osTicket\include\ost-config.php"}}$
  - Right click **_”ost-config.php”_** and click **_"Properties"_**
  - Navigate to the **_”Security”_** tab
  - Select **_”Advanced”_**
  - Click **_”Disable inheritance”_**, followed by:
  > **_”Remove all inherited permissions from this object”_** on the Block Inheritance Prompt
  - Click **_”Add”_** → **_”Select a principal”_**
  - Under **_”Enter the object name to select”_** field, write: $\color{#d97706}{\text{(YOUR DESIRED USER HERE)}}$ → click **_”Check Names”_** → **_”OK”_**
  - Below **_"Basic Permissions"_** Check ✔ **_"Full control"_** → **_"OK"_**
  - **_”Apply”_** changes → select **_”OK”_**
</p>
<br />
<p>
  
<img width="825" height="741" alt="image" src="https://github.com/user-attachments/assets/e06c5962-8e2f-47b7-a771-fa8ae84b6b05" />
  
  __Step 7__: Complete osTicket Web Setup:
  - Refresh the osTicket installer web page → select **_“Continue“_**
  - Fill out **_"System Settings"_** → **_"Admin User"_** → **_"Database Settings"_** fields
  - Select **_"Install Now"_**
</p>
<br />
<p>
  
  __Step 8__: (Optional) Clean up and Finalize setup:
  - Delete the setup folder: C:\inetpub\wwwroot\osTicket\setup
  - Set Permissions to **_“Read”_** only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<br />
<p>
  
Congratulations! Hopefully, the installation has been completed without any errors.
</p>
<img width="825" height="741" alt="image" src="https://github.com/user-attachments/assets/b53a18f8-af68-4fb6-b22f-75baf2c10ae2" />
</p>
<br />
<p>
  
 __Useful Links__:
  - Help Desk login URL: http://localhost/osTicket/scp/login.php
  - End Users osTicket URL: http://localhost/osTicket/
  - osTicket All-In-One Download: https://drive.google.com/file/d/1ToJ3W8Ej9Qx1yRb68MPDhTkmsmUg5aCH/view?usp=sharing
</p>
<br />
