<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket - Prerequisites and Installation

In this home lab, I will deploy and configure osTicket on an Azure Windows VM to demonstrate and refine both my administrative and user management skills.

## Environments and Technologies Used

- **Microsoft Azure** (Virtual Machines/Compute)
- **Remote Desktop**
- **Internet Information Services (IIS)**

## Operating Systems Used 

- **Windows 10** (21H2)

## Installation Steps

### 1. Create an Azure Virtual Machine (Windows 10, 4 vCPUs)
- **Name:** osticket-vm
- **Username:** labuser
- **Password:** osTicketPassword1!

### 2. Log into the VM with Remote Desktop

### 3. Download and Unzip osTicket Files
- Download the osTicket-Installation-Files.zip and unzip it on your desktop. The folder should be called “osTicket-Installation-Files”.

### 4. Install / Enable IIS with CGI Support
- Go to **World Wide Web Services -> Application Development Features** and ensure **CGI** is selected.
  
![r1](https://github.com/user-attachments/assets/a1ad723b-bb77-4e3a-8dd3-2aa42d7b1352)

### 5. Install PHP Manager for IIS
- From the “osTicket-Installation-Files” folder, install **PHP Manager for IIS** (PHPManagerForIIS_V1.5.0.msi).

### 6. Install the Rewrite Module
- Install the **Rewrite Module** (rewrite_amd64_en-US.msi).
  
![r2](https://github.com/user-attachments/assets/4ba270b7-c3c5-4e66-beb3-01afaabc87d6)

### 7. Set Up PHP Folder
- Create the directory **C:\PHP**.
- Unzip **PHP 7.3.8** (php-7.3.8-nts-Win32-VC15-x86.zip) into **C:\PHP**.

### 8. Install Required Software
- From the “osTicket-Installation-Files” folder, install **VC_redist.x86.exe** and **MySQL 5.5.62** (mysql-5.5.62-win32.msi).
  - Choose **Typical Setup** and launch the configuration wizard after installation.
  - Configure with:
    - **Username:** root
    - **Password:** root
  
![r3](https://github.com/user-attachments/assets/afa783f2-b271-4e83-a0e4-0c7fdee79d5b)
![r4](https://github.com/user-attachments/assets/4a5b4d83-3cfa-4d42-815a-7db5a9b3171c)

### 9. Register PHP with IIS
- Open IIS as an admin.
- Register PHP from within IIS: **PHP Manager -> C:\PHP\php-cgi.exe**.
- Reload IIS by stopping and starting the server.
  
![r5](https://github.com/user-attachments/assets/b77a4b94-b283-47a1-bb8a-f17f314235ff)

### 10. Install osTicket v1.15.8
- From the “osTicket-Installation-Files” folder, unzip **osTicket-v1.15.8.zip** and copy the **upload** folder to **C:\inetpub\wwwroot**.
- Rename the folder to **osTicket** (Ensure there are no spaces in the name).
  
![r6](https://github.com/user-attachments/assets/a878a84b-d23a-404d-9833-6a78e89415b5)

### 11. Enable PHP Extensions
- Go back to IIS -> **Sites -> Default -> osTicket**.
- Open **PHP Manager** and enable the following extensions:
  - **php_imap.dll**
  - **php_intl.dll**
  - **php_opcache.dll**

  Refresh the site in your browser.

![r7](https://github.com/user-attachments/assets/1b6d2a15-0f01-40dd-915b-e5a9e8d7d838)
![r8](https://github.com/user-attachments/assets/d08e9128-55e7-4e49-896f-9ae272dfbfd4)

### 12. Rename `ost-sampleconfig.php` to `ost-config.php`
- Navigate to **C:\inetpub\wwwroot\osTicket\include** and rename **ost-sampleconfig.php** to **ost-config.php**.
  
![r9](https://github.com/user-attachments/assets/ccfa54ea-949c-4537-be17-3b52da2f9fc5)

### 13. Set Permissions for `ost-config.php`
- Right-click on **ost-config.php**, disable inheritance, remove all permissions, and grant **Everyone** full control.
  
![r10](https://github.com/user-attachments/assets/449e83c2-2ba1-4db6-b605-b54c38068f17)
![r11](https://github.com/user-attachments/assets/c5b1b44b-c8ed-4b9c-ace3-8e58da3e86fc)

### 14. Continue osTicket Setup in the Browser
- Access the setup page via **http://localhost/osTicket/scp/login.php**.
- Fill in the required details:
  - **Name Helpdesk**
  - **Default email** (receives emails from customers)

![r12](https://github.com/user-attachments/assets/6670af29-8e66-4260-a2bc-3906e211c672)

### 15. Set Up the MySQL Database
- Open **HeidiSQL** and create a session using the username and password: **root/root**.
- Create a new database called **osTicket**.

![r13](https://github.com/user-attachments/assets/9e218778-aa55-465e-9d43-1590732b4cf1)

### 16. Complete osTicket Setup
- In the browser, configure MySQL details:
  - **MySQL Database:** osTicket
  - **MySQL Username:** root
  - **MySQL Password:** root
- Click **Install Now!**.

![r14](https://github.com/user-attachments/assets/ac505e81-ecdf-4a0c-bcde-3e2c07416254)
![r15](https://github.com/user-attachments/assets/6fc00a22-6fa3-4f9a-882e-a58834095336)

### 17. Access osTicket
- Once installed, access the help desk login page: **http://localhost/osTicket/scp/login.php**.

![r16](https://github.com/user-attachments/assets/d9c07532-1d8a-4f6d-9735-bf1bec241964)

- End User's osTicket URL: **http://localhost/osTicket/**.

![r17](https://github.com/user-attachments/assets/56d53eca-76a5-4f82-8b7f-9ef320efbaa9)

## Takeaways and Key Skills Developed

In this project, I successfully installed and set up **osTicket** on an Azure Windows VM to practice both admin and user skills. I configured the VM with **Windows 10**, installed **IIS**, **PHP**, and **MySQL** to support osTicket, and learned how to install and configure essential dependencies like **PHP Manager** and the **Rewrite Module**. The process also involved setting up and configuring **PHP extensions**, managing permissions, and creating a MySQL database. This project improved my understanding of web-based application installation, PHP configuration, and database management while also helping me troubleshoot issues during installation and configuration. It also provided hands-on experience with **Azure VM** setup and managing **Windows IIS** servers.
