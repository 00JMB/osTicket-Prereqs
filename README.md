<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

# osTicket: Prerequisites and Installation

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
* Drag the newly downloaded folder onto the desktop
* Right-click the folder > **Extract All** > Ensure extraction to the desktop

### 2. Enable IIS Features
* Open **Control Panel** > **Programs** > **Programs and Features** > **Turn Windows features on or off**
* Check the **Internet Information Services** box
* Expand **World Wide Web Services** > **Application Development Features** > Check the **CGI** box

### 3. Install PHP and IIS Modules
* Install **PHPManager for IIS** (Run `PHPManagerForIIS_V1.5.0.msi`)
* Install the **URL Rewrite Module** for IIS
* Create a new directory in the **C:** drive named **PHP**
* Extract **php-7.3.8-nts-Win32-VC15-x86** into the **PHP** directory
* Run the **VC_redist.x86** installer

### 4. Install MySQL
* Run the **MySQL Installer** (`mysql-5.5.62-win32`) > **Typical** > **Install**
* Launch the **MySQL Configuration Wizard**
* Choose and confirm a **root password** (keep track of this!)
* Click **Execute** > **Finish**

### 5. Register PHP with IIS
* **Start** > Search **IIS** > Run **Internet Information Services Manager** as administrator
* **PHP Manager** > **Register a new PHP version** > Browse to `C:\PHP` > Select **php-cgi** > Click **Open** > **Ok**

### 6. Install osTicket
* Extract the **osTicket-v1.15.8** file
* Open the **Upload** folder
* Navigate to `C:\inetpub\wwwroot`
* Copy the **upload** folder into **wwwroot**
* Rename **upload** folder to **osTicket**
* Restart the server

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

### Congrats, you're ready to move on to the next phase: **<a href="https://github.com/JBeezy888/osTicket-Post-Installation-Configuration">osTicket: Post-Installation Configuration**
