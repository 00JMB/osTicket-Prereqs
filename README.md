<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket: Prerequisites and Installation</h1>

This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system, osTicket.

---

## 💻 Environments and Technologies Used
* **Microsoft Azure:** Virtual Machines/Computer
* **Remote Desktop**
* **Internet Information Services (IIS)**

---

## 🖥️ Operating Systems Used
* **Windows 10 (21H2)**

---

## ✅ List of Prerequisites
* A Windows desktop or Virtual Machine running Windows 10 Pro with at least 2 vCPUs

---

## 🚀 Installation Steps

### 1. Download Required Files
* Run your Virtual Machine or Desktop and head to the attached link to install all necessary files and software dependencies for osTicket: [Download Installation Files](https://drive.google.com/file/d/1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD/view?usp=drivesdk)
* Open File Explorer and navigate to the **Downloads** folder
* **Right-click** the newly downloaded folder > **Extract All**
  ![image](https://github.com/user-attachments/assets/67b397bc-ade0-44b2-98ee-1d398f626888)

* Ensure extraction to the **desktop**
  ![image](https://github.com/user-attachments/assets/85352255-0e1b-4e0a-b076-c568b56f8067)

### 2. Enable IIS Features
* Open **Control Panel** > **Programs**
  ![image](https://github.com/user-attachments/assets/86da782b-8ebe-4980-af16-4ed7ffc03e2b)

* **Programs and Features** > **Turn Windows features on or off**
  ![image](https://github.com/user-attachments/assets/ca6e101e-d254-4bfe-89d0-4853afbe67b5)

* Check the **Internet Information Services** box
* Check **Web Management Tools**, Check & Expand **World Wide Web Services** > **Application Development Features** > Check the **CGI** box
  ![image](https://github.com/user-attachments/assets/58505e11-7daf-44d8-b8ae-fe4d26071caf)

* The computer will recommened you **restart** so the changes take effect, let it
  ![image](https://github.com/user-attachments/assets/642b4de0-b9e6-4f53-9fb4-83e266d61094)



### 3. Install PHP and IIS Modules
**In the extracted osTicket Installation Folder**
* Install **PHPManager for IIS** (Run `PHPManagerForIIS_V1.5.0.msi`)
  ![image](https://github.com/user-attachments/assets/314f4808-a734-4976-8c18-276e9cb64d98)
  ![image](https://github.com/user-attachments/assets/b45dfe93-f112-4259-aa6c-b83bf2b1125f)

* Install the **URL Rewrite Module** for IIS
  ![image](https://github.com/user-attachments/assets/dbf2c6ec-d970-4e68-9f38-33881b0bc2f5)
  ![image](https://github.com/user-attachments/assets/3c8075ae-0a43-402a-88ef-db9bd51954c5)

* Create a new directory in the **(C:)** drive named **PHP**
  ![image](https://github.com/user-attachments/assets/78cccd75-1194-421b-aac4-c2ce496108c3)

* Extract **php-7.3.8-nts-Win32-VC15-x86** into the **PHP** directory
  ![image](https://github.com/user-attachments/assets/c367078d-1f13-46eb-9254-6c7669eac653)
  ![image](https://github.com/user-attachments/assets/bdcd71fc-5019-4bdd-9988-5273ef52100c)

* Run the **VC_redist.x86** installer
  ![image](https://github.com/user-attachments/assets/981e6d60-b23d-4528-9b7f-5dfe30828bb5)

### 4. Install MySQL
* Run the **MySQL Installer** (`mysql-5.5.62-win32`) > **Typical** > **Install**
* Launch the **MySQL Configuration Wizard**
   ![image](https://github.com/user-attachments/assets/ffd4a44e-ca93-4891-a931-51b9b546f677)

* **Standard Configuration** > **Next**
* Next we have to **set a root password**, for the purposes of this project, set it as **root**
  ![image](https://github.com/user-attachments/assets/e14e82db-c05e-4c43-bac0-0813c7eedc01)

* Click **Execute** > **Finish**
  ![image](https://github.com/user-attachments/assets/359632d3-679f-412b-9843-0468c850ae50)


### 5. Register PHP with IIS
* **Start** > Search **IIS** > Run **Internet Information Services Manager** as administrator
  ![image](https://github.com/user-attachments/assets/b1359c0f-6061-486f-a9fc-db8440c32016)

* Double-click **PHP Manager**
  ![image](https://github.com/user-attachments/assets/46202635-6c7d-4281-a01f-b2d3530655b4)
  
* **Register a new PHP version**
  ![image](https://github.com/user-attachments/assets/83771986-dec8-4064-b7b2-41a70bb7a37f)

* **Browse to `C:\PHP`**
  ![image](https://github.com/user-attachments/assets/4dbb5755-5f44-4a97-8bf3-0a6aa45e3eec)

* Select **php-cgi**
  ![image](https://github.com/user-attachments/assets/1f53e182-9387-4707-9615-0c56539530d9)

* Click **Open** > **Ok**
  ![image](https://github.com/user-attachments/assets/38db1c03-20f9-45e9-a312-7a5ab9260e6a)


### 6. Install osTicket
* Extract the **osTicket-v1.15.8** file
  ![image](https://github.com/user-attachments/assets/bca13bd5-0094-48a7-8ccd-caf4a886ec14)

* Open extracted folder > **copy** the **Upload** folder
  ![image](https://github.com/user-attachments/assets/221f013a-2197-4c73-9c97-f89bd4148cd5)

* Navigate to `C:\inetpub\wwwroot` in File Explorer
* **Paste** the **upload** folder into **wwwroot**
  ![image](https://github.com/user-attachments/assets/1b4363ec-8c45-4515-ab07-19ee1b3e2098)

* Rename **upload** folder to **osTicket**
  ![image](https://github.com/user-attachments/assets/be99e50b-f7de-43f9-8e63-939027dbeece)

* Then just **delete the original upload folder**
   ![image](https://github.com/user-attachments/assets/247d4fdb-981e-46dc-912a-9a9862b70a39)


* **Back in PHP Manager:** Restart the server
  ![image](https://github.com/user-attachments/assets/15288b69-90cd-4699-a0f8-ac398b50c4a4)


---

## 🔥 Test Run
* Expand **osTicket** under the **Connections** tab
* Expand **Sites** > **Default Web Site** > **osTicket**
* Click **Browse** under **Manage Folder**

---

## 🛠️ Additional Setup and Configuration

If all steps were followed correctly, you’ll see this:

Next we’re going enable a few of the disabled extensions (marked by the Xs on the left) for our web server, this is to ensure everything works as it should.

* Head back into the IIS Manager > Sites > Default Side > osTicket > Open PHP Manager > Scroll down a bit and you’ll see the “PHP Extensions” section, under that you’ll see “Enable or disable an extension, click that
* Here we’ll enable the required extensions: “php_imap.dll” “php_intl.dll” & “php_opcache.dll”
* Close IIS, and refresh the osTicket site.

Next we’re going to edit a file osTicket needs to make configurations (and give osTicket the permissions it needs to function properly)

* In the File Explorer: C:\inetpub > wwwroot > osTicket > include > In this folder there is a file named “ost-sampleconfig.php”, RENAME it “ost-config.php” (exactly as shown!)
* Right click the same file and click “Properties” > “Security” Tab > “Advanced” > “Disable Inheritance” > “Remove all…”
* Add new permissions: click “add” > “Select a principle” > Type “everyone” > Press enter > Check “Full Control” > Click “Apply” > “OK”

Head back to the osTicket site and click “Continue”.

---

### 🛜 Database Setup

* Install **HeidiSQL** > Run through the installer > Launch **HeidiSQL**
* Click **New** > Enter the root Username and Password > Click **Open**
* Right click the “Unnamed” tab > **Create new** > **Database**
* Name the database **osTicket** > Click **OK**

### Back to the osTicket site: 

* Add the Database name, Username, and Password
* Click **Install Now**

---

### Congrats, you're ready to move on to the next phase: **<a href="https://github.com/00JMB/osTicket-Post-Installation-Configuration">osTicket: Post-Installation Configuration**
