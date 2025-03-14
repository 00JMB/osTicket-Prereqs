<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket: Prerequisites and Installation

This guide provides a step-by-step walkthrough for setting up osTicket, an open-source help desk ticketing system.

---

## 💻 Environments and Technologies Used
* **Microsoft Azure** – Virtual Machines/Computing Environment
* **Remote Desktop** – For server access and management
* **Internet Information Services (IIS)** – Web server for hosting osTicket

---

## 🖥️ Operating Systems Used
* **Windows 10 (21H2)**

---

## 🎯 Post-Installation Configuration Objectives

* Download Required Files
* Enable IIS Features
* Install PHP and IIS Modules
* Install MySQL
* Register PHP with IIS
* Install osTicket
* Test Run
* Configure Web Server
* Set Up Database

---

## ✅ Prerequisites
* A Windows desktop or Virtual Machine running **Windows 10 Pro** with at least **2 vCPUs**

---

## 🚀 Installation Steps

### 1️⃣ Download Required Files
* Start your **Virtual Machine or Desktop**.
* Download the required installation files from the following link: [Download Installation Files](https://drive.google.com/file/d/1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD/view?usp=drivesdk).
* Open **File Explorer**, navigate to the **Downloads** folder, and extract the downloaded folder to your **Desktop**.
  ![image](https://github.com/user-attachments/assets/67b397bc-ade0-44b2-98ee-1d398f626888)
  ![image](https://github.com/user-attachments/assets/85352255-0e1b-4e0a-b076-c568b56f8067)

---

### 2️⃣ Enable IIS Features
* Open **Control Panel** > **Programs**.
  ![image](https://github.com/user-attachments/assets/86da782b-8ebe-4980-af16-4ed7ffc03e2b)
  
* Navigate to **Programs and Features** > **Turn Windows features on or off**.
  ![image](https://github.com/user-attachments/assets/ca6e101e-d254-4bfe-89d0-4853afbe67b5)
  
* Enable **Internet Information Services (IIS)** and **Web Management Tools**.
* Under **World Wide Web Services**, expand **Application Development Features** and enable **CGI**.
  ![image](https://github.com/user-attachments/assets/58505e11-7daf-44d8-b8ae-fe4d26071caf)


---

### 3️⃣ Install PHP and IIS Modules
* Inside the extracted osTicket Installation folder on the desktop:
  * Run `PHPManagerForIIS_V1.5.0.msi` to install **PHP Manager for IIS**.
    ![image](https://github.com/user-attachments/assets/314f4808-a734-4976-8c18-276e9cb64d98)
    ![image](https://github.com/user-attachments/assets/b45dfe93-f112-4259-aa6c-b83bf2b1125f)
    
  * Install the **URL Rewrite Module**.
    ![image](https://github.com/user-attachments/assets/dbf2c6ec-d970-4e68-9f38-33881b0bc2f5)
    ![image](https://github.com/user-attachments/assets/3c8075ae-0a43-402a-88ef-db9bd51954c5)
    
* Create a new directory in `C:` named **PHP** then, move `php-7.3.8-nts-Win32-VC15-x86` into this directory.
  ![image](https://github.com/user-attachments/assets/f7b569dd-dd26-466d-bd9e-67cd8c8bcf3f)

  * Now, Extract the folder into this directory.
  ![image](https://github.com/user-attachments/assets/6594533a-db72-445e-8976-59fd61b22c9b)

* **Back in the desktop folder:** Run the **VC_redist.x86** installer to ensure necessary runtime components are installed.
  ![image](https://github.com/user-attachments/assets/981e6d60-b23d-4528-9b7f-5dfe30828bb5)


---

### 4️⃣ Install MySQL
* Run the **MySQL Installer** (`mysql-5.5.62-win32`) and select **Typical Installation**.
* Open the **MySQL Configuration Wizard**.
  ![image](https://github.com/user-attachments/assets/ffd4a44e-ca93-4891-a931-51b9b546f677)
  
* Choose **Standard Configuration** > **Next**.
* Set the root password to **root** for this setup.
  ![image](https://github.com/user-attachments/assets/e0b1d64c-fec4-42a2-a919-fbd7638802f8)

  
* Click **Execute**, then **Finish**.
  ![image](https://github.com/user-attachments/assets/359632d3-679f-412b-9843-0468c850ae50)


---

### 5️⃣ Register PHP with IIS
* Open **Internet Information Services (IIS) Manager** as Administrator.
  ![image](https://github.com/user-attachments/assets/b1359c0f-6061-486f-a9fc-db8440c32016)
  
* Double-click **PHP Manager**.
  ![image](https://github.com/user-attachments/assets/46202635-6c7d-4281-a01f-b2d3530655b4)
  
* Click **Register a new PHP version**.
  ![image](https://github.com/user-attachments/assets/83771986-dec8-4064-b7b2-41a70bb7a37f)
  
* Navigate to `C:\PHP`, select **php-cgi.exe**, and confirm.
  ![image](https://github.com/user-attachments/assets/4dbb5755-5f44-4a97-8bf3-0a6aa45e3eec)
  ![image](https://github.com/user-attachments/assets/1f53e182-9387-4707-9615-0c56539530d9)


---

### 6️⃣ Install osTicket
* Extract **osTicket-v1.15.8**.
  ![image](https://github.com/user-attachments/assets/bca13bd5-0094-48a7-8ccd-caf4a886ec14)
  
* Copy the **Upload** folder to `C:\inetpub\wwwroot` and rename it to **osTicket**.
  ![image](https://github.com/user-attachments/assets/221f013a-2197-4c73-9c97-f89bd4148cd5)
  ![image](https://github.com/user-attachments/assets/be99e50b-f7de-43f9-8e63-939027dbeece)
  
* Restart IIS from **PHP Manager**.
  ![image](https://github.com/user-attachments/assets/15288b69-90cd-4699-a0f8-ac398b50c4a4)


---

### 7️⃣ Test Run
* In IIS Manager, expand **Sites** > **Default Web Site** > **osTicket**.
* Click **Browse** under **Manage Folder**.
* If everything is set up correctly, the osTicket installation page should load.


---

### 8️⃣ Web Server Configuration
* Open IIS Manager and navigate to **Sites > Default Web Site > osTicket**.
* In **PHP Manager**, enable the following extensions:
  - `php_imap.dll`
  - `php_intl.dll`
  - `php_opcache.dll`
* Navigate to `C:\inetpub\wwwroot\osTicket\include` and rename `ost-sampleconfig.php` to `ost-config.php`.
* Adjust file permissions:
  - Right-click `ost-config.php` > **Properties** > **Security** > **Advanced**.
  - Click **Disable Inheritance** > **Remove all inherited permissions**.
  - Add a new permission: **Select a principal** > Enter `everyone` > **Full Control** > Apply changes.
* Refresh the osTicket installation page and proceed.


---

### 9️⃣ Database Setup
* Install **HeidiSQL** and open the application.
* Create a new connection using `root` as the username and password.
* Right-click in the left panel and select **Create New > Database**.
* Name the database **osTicket**.

#### Complete the osTicket Installation:
* Return to the osTicket web page.
* Enter the database details:
  - Database Name: `osTicket`
  - Username: `root`
  - Password: `root`
* Click **Install Now**.

---

### 🎉 Congratulations!
You’ve successfully installed osTicket.
Next steps: [osTicket Post-Installation Configuration](https://github.com/00JMB/osTicket-Post-Installation-Configuration)
