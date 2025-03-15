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

  * Now, Extract the folder into this directory. After the extraction, you can delete the zip
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
    ![image](https://github.com/user-attachments/assets/ecf766be-bfbc-4e98-b9f4-28d0afa0ffd8)
    ![image](https://github.com/user-attachments/assets/be99e50b-f7de-43f9-8e63-939027dbeece)
  
* Restart IIS from **PHP Manager**.
    ![image](https://github.com/user-attachments/assets/15288b69-90cd-4699-a0f8-ac398b50c4a4)


---

### 7️⃣ Test Run
* In IIS Manager, expand **Sites** > **Default Web Site** > **osTicket**.
* Click **Browse** on the right-hand side, under **Manage Folder**.
  ![image](https://github.com/user-attachments/assets/d0af2fc8-a069-4eb0-b9e1-12c0d480833b)

* If everything is set up correctly, this osTicket page should load.
    ![image](https://github.com/user-attachments/assets/852dca1c-e554-4669-997d-6047de767948)


---

### 8️⃣ Web Server Configuration
* Open IIS Manager and navigate to **Sites > Default Web Site > osTicket**.
* Open **PHP Manager** and navigate to **PHP Extensions > Enable or disable extensions**
    ![image](https://github.com/user-attachments/assets/8eeb0266-b5ec-48b4-a9fb-aa4e1d5a0fa2)

* We're going to enable the following extensions:
  - `php_imap.dll`
  - `php_intl.dll`
  - `php_opcache.dll`
      ![image](https://github.com/user-attachments/assets/87f3e62d-7298-43d3-8e5d-34beb24c67ec)

* Navigate to `C:\inetpub\wwwroot\osTicket\include` and **rename** `ost-sampleconfig.php` to `ost-config.php`.
    ![image](https://github.com/user-attachments/assets/b4f67982-6e05-47b4-b043-07fda0924b37)
    ![image](https://github.com/user-attachments/assets/3b5b9caa-ac85-4434-95df-363d965d0c59)

* Adjust file permissions:
  - Right-click `ost-config.php` > **Properties** > **Security** > **Advanced**.
      ![image](https://github.com/user-attachments/assets/c2f96440-ce6f-43c9-8c9b-e7d78c7b10c0)
      ![image](https://github.com/user-attachments/assets/027cc67a-9ea0-4cd0-8f15-5f497af2fae0)

  - Click **Disable Inheritance** > **Remove all inherited permissions**. > **Apply > OK**.
      ![image](https://github.com/user-attachments/assets/04b6dd67-faed-4664-85bf-aa89a91ccf2c)
      ![image](https://github.com/user-attachments/assets/636410ba-9ed7-403c-9b94-5895e8f21d61)

  - **Add** a new permission: **Select a principal** > Enter `everyone` > **Check Names > OK**.
      ![image](https://github.com/user-attachments/assets/71de496a-e02a-4f92-9261-9f591bcd42fe)

  - **Full Control** > **Apply changes**.
      ![image](https://github.com/user-attachments/assets/97b282a5-ed6b-442a-861f-255f04bfcba7)

* Refresh the osTicket installation page and proceed.
  - *You'll notice that our changes have taken effect, and new permissions have been added*
      ![image](https://github.com/user-attachments/assets/d80a9a77-2796-4c6c-96e4-538a767bdee0)



---

### 9️⃣ Database Setup
* **Back in the osTicket Installation Files Folder:** Install **HeidiSQL**, *Leave all settings as-is*
* Launch HeidiSQL after installation > skip the update
* **Create a new connection using `root` as the username and password**. > **Click Open**
      ![image](https://github.com/user-attachments/assets/d14b63d9-9615-4018-9fa3-9b9766aca126)
      ![image](https://github.com/user-attachments/assets/7019750a-01a9-45a3-a281-474e6cc5a770)

* Right-click *Unnamed* in the left panel, and select **Create New > Database**.
      ![image](https://github.com/user-attachments/assets/f42f9f1a-2f5b-4dec-9201-72dc96f9782c)

* Name the database **osTicket**.
      ![image](https://github.com/user-attachments/assets/83d3b893-33e7-4d79-9b3d-73f6cb00bfe9)
      ![image](https://github.com/user-attachments/assets/32743221-fce9-41e1-827e-1917632ffb61)


#### Complete the osTicket Installation:
* Return to the osTicket web page. > click *Continue*
* Fill out the log in info that your going to use
      ![image](https://github.com/user-attachments/assets/e5f79a66-21cb-4ae4-933e-00eeace11f28)

* Enter the SQL database details at the bottom of the page:
  - Database Name: `osTicket`
  - Username: `root`
  - Password: `root`
        ![image](https://github.com/user-attachments/assets/afe21d6a-7bfe-4f9d-a92d-83c5aaa89faf)

* Click **Install Now**.
    ![image](https://github.com/user-attachments/assets/132de29b-5a9c-4f23-bf0d-7a0b4ade87c0)


---

### 🎉 Congratulations!
You’ve successfully installed osTicket.
When you're ready to move on to the next phase, Follow this link: **<a href="https://github.com/00JMB/osTicket-Post-Installation-Configuration">osTicket: Post-Installation Configuration**
