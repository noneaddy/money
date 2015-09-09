# Mobile Security Framework (MobSF) Configuration

***

## Requirements

Python 2.7

Oracle JDK 1.7 or above [http://www.oracle.com/technetwork/java/javase/downloads/](http://www.oracle.com/technetwork/java/javase/downloads/)

**NOTE:**
On Linux and Mac, install Oracle Java and **make it the default** one.

iOS IPA Binary Analysis requires MAC OS X and you need to install Commandline tools for MAC OS X 
[http://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/](http://osxdaily.com/2014/02/12/install-command-line-tools-mac-os-x/)

##Download

Download the latest version of Mobile Security Framework (MobSF) from here: [https://github.com/ajinabraham/Mobile-Security-Framework-MobSF/releases](https://github.com/ajinabraham/Mobile-Security-Framework-MobSF/releases)

Download MobSF VM 0.1 ova file: [https://goo.gl/CiTB12](https://goo.gl/CiTB12)
(Download only if you need Dynamic Analysis)

##Installation

### Windows
Extract the MobSF compressed file to C:\MobSF
### Mac
Extract MobSF compressed file to /Users/[username]/MobSF
### Linux
Extract MobSF compressed file to /home/[username]/MobSF

## Configuring Static Analyzer
**Tested on Windows 7, 8, 8.1, 10, Ubuntu, OSX Mavericks**

Install MobSF Python dependencies using **pip**

### Windows
`C:\Python27\Scripts\pip.exe install -r requirements.txt`

**NOTE**: If pip.exe is not available in Scripts directory, download and install latest Python2.7 from [https://www.python.org/downloads/](https://www.python.org/downloads/) 

### Unix
`pip.exe install -r requirements.txt`

###Running MobSF

`python manage.py runserver`

If you need to run on a specific port number try  `python manage.py runserver PORT_NO`

If everything goes right, you will get an output like

![Mobile Security Framework (MobSF) Running](https://cloud.githubusercontent.com/assets/4301109/9768322/6e7f4846-5740-11e5-9933-81fa87b566a8.png)
***
