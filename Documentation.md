# Mobile Security Framework (MobSF) Configuration

***

## Requirements

* Python 2.7 - [https://www.python.org/downloads/](https://www.python.org/downloads/) 
* Oracle JDK 1.7 or above - [http://www.oracle.com/technetwork/java/javase/downloads/](http://www.oracle.com/technetwork/java/javase/downloads/)
* Oracle VirtualBox - [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
* iOS IPA binary analysis requires MAC OS X and you need to install Command-line tools for MAC OS X 
[http://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/](http://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/)
* Hardware Requirements: Min 4GB RAM and 5GB HDD.

**NOTE:**
* On Linux and Mac, install Oracle Java 1.7 or above and **make it the default** one.

##Download

* Download latest release of MobSF: [https://github.com/ajinabraham/Mobile-Security-Framework-MobSF/releases](https://github.com/ajinabraham/Mobile-Security-Framework-MobSF/releases)
* Download MobSF VM 0.1 ova file: [https://goo.gl/CiTB12](https://goo.gl/CiTB12)
(Download only if you need Dynamic Analysis)

##Installation
**Tested on Windows 7, 8, 8.1, 10, Ubuntu, OSX Mavericks**

* **Windows**: Extract the MobSF compressed file to C:\MobSF
* **Mac**: Extract MobSF compressed file to /Users/[username]/MobSF
* **Linux**: Extract MobSF compressed file to /home/[username]/MobSF

## Configuring Static Analyzer

Install MobSF Python dependencies using **pip**

#### Windows
`C:\Python27\Scripts\pip.exe install -r requirements.txt`

**NOTE**: If pip.exe is not available in Scripts directory, Download and Re-install latest Python2.7.

#### Unix
`pip.exe install -r requirements.txt`

## Running MobSF

`python manage.py runserver`

If you need to run on a specific port number try  `python manage.py runserver PORT_NO`

If everything goes right, you will get an output like the one below.

![Mobile Security Framework (MobSF) Running](https://cloud.githubusercontent.com/assets/4301109/9768322/6e7f4846-5740-11e5-9933-81fa87b566a8.png)

***

## Configuring Dynamic Analyzer

Dynamic Anlayzer is available only for Android binaries (APK) and works only if your laptop has at least 4GB of RAM and Full Virtualisation support.

To Configure Dynamic Analyzer we need 4 things.
* VM UUID
* Snapshot UUID
* Host/Proxy IP
* VM/Device IP
 
### Steps to Follow

* Open VirtualBox, Go to **File -> Import Appliance** and select the MobSF_VM_X.X.ova file.
  ![Importing MobSF VM ova file](https://cloud.githubusercontent.com/assets/4301109/9768972/cbdd115e-5744-11e5-88dc-bf280df3a963.png)
* Accept the GPL3 Licence and Complete the import process. Do not alter anything.
* Once the OVA is Imported Successfully, you will see a new entry in VirtualBox named MobSF_VM_X.X
* Right Click MobSF VM and Choose Settings, Go to Network tab. Here we need to configure two Network Adapters.
  
  * **Adapter** 1 should be enabled and attached to **Host-only Adapter**. Remember the name of the adapter. We need the name to Identify the Host/Proxy IP.
    
    ![Adapter 1](https://cloud.githubusercontent.com/assets/4301109/9769043/2852d5b8-5745-11e5-9da4-0d76c18ecc3b.png)
  
  * **Adapter 2** should be enabled and attached to **NAT**
    
    ![Adapter 2](https://cloud.githubusercontent.com/assets/4301109/9769162/14556a70-5746-11e5-8d76-ce8d6d200167.png)

* Save the settings and Start MobSF VM. While the VM is Booting up. Note down the **VM IP**.
  
  ![VM IP](https://cloud.githubusercontent.com/assets/4301109/9769219/794771da-5746-11e5-9d81-5549422aac71.png)
* Once the VM Boots up, It will present a Lock Screen. The password for the Lock Screen is `1234`
  
  ![MobSF VM](https://cloud.githubusercontent.com/assets/4301109/9769278/c35e0f90-5746-11e5-9d07-75c1c63e8cdb.png)
  
  **NOTE**: If the VM does not boot up properly then you cannot perform Dynamic Analysis.
* **Getting the Host/Proxy IP**
  * **Windows** : Issue the command `ipconfig` in command prompt and note down the IP corresponding to the name of the Host-only Adapter.

    ![ipconfig example windows](https://cloud.githubusercontent.com/assets/4301109/9769557/8fdcf3d2-5748-11e5-905e-927159ea525b.png)

  * **Unix** : Issue the command `ifconfig` in terminal and note down the IP corresponding to the name of the Host-only Adapter.

    ![ifconfig example in mac](https://cloud.githubusercontent.com/assets/4301109/9769553/88bb329e-5748-11e5-9e91-3d14db839771.png)
    
* Go to Wi-Fi Settings in MobSF VM and set the Proxy IP as the Host/Proxy IP which you obtained in the previous step and port no as `1337`.

![Proxy Settings in VM](https://cloud.githubusercontent.com/assets/4301109/9769738/92961788-5749-11e5-98ac-26488ca46516.png)

* Save the settings and Navigate to the Home Screen of the MobSF VM. Wait for 30 Seconds and save a snapshot of the MobSF VM in VirtualBox

![Saving MobSF VM Snapshot](https://cloud.githubusercontent.com/assets/4301109/9769841/26555556-574a-11e5-9de2-c7eb8b0f30bf.png)

* Once the Snapshot is saved, right click MobSF VM and select `Show in Explorer` or `Show in Finder`.

[https://cloud.githubusercontent.com/assets/4301109/9769901/83c30b3e-574a-11e5-8f90-6ac02732429a.png](Show VM Files)

* Open the File **MobSF_VM_X.X.vbox** in any Text Editor and note down the VM UUID and Snapshot UUID

![Getting VM UUID and Snapshot UUID](https://cloud.githubusercontent.com/assets/4301109/9769959/e9d9bb0c-574a-11e5-8005-730306445be9.png) 
Here `uuid` is the VM UUID and `currentSnapshot` is the Snapshot UUID.

* Now we have all the things needed to configure the Dynamic Analyzer (Host/Proxy IP, VM IP, VM UUID and Snapshot UUID)

* Go to `MobSF/settings.py` and set the appropriate values as

  * UUID = VM UUID
  * SUUID = Snapshot UUID
  * VM_IP = VM IP
  * PROXY_IP = Host/Proxy IP 
  
  A sample configuration is shown below
  ![Settings](https://cloud.githubusercontent.com/assets/4301109/9770080/9490e8f4-574b-11e5-9548-a2b138ab4155.png)
  
  
* Finally start the server.