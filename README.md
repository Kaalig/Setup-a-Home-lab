# Setup-a-Home-lab

Basically a simple walkthrough of setting up a Home Lab using a type II hypervisor, which basically means a Virtual Machine. For this project we will setup an offensive machine and a defensive machine, both UNIX distribution, and we will simulate an attack between the machines with both perspectives. I will go with the easiest to use and most known offensive linux distribution : Kali Linux. For our defensive machine, I will go with the lastest version of Ubuntu, as I am emulating a normal user account. 

## Step 1 : Downloading a virtualization software

There is plenty of good and renowed virtualization software, we will go with Oracle Virtual Box on this one. 

For the download, simply go to : https://www.virtualbox.org/wiki/Downloads and download your OS package.

### 1.1 Installation 

If you are using Windows :
- Open the .exe file and just keep installing using the graphical interface like you would do for any other application.


If you already are using Linux, type this command : 

```
sudo apt upgrade
sudo apt install virtualbox
```
Note : I tend to always upgrade my distribution before installing something on Linux in order to not have any weird problems. It's better to prevent than to repair !

### 1.2 Installing extension package

Extension package of VirtualBox is not a necessity but it gives some interesting feature like USB 2.0/3.00 , Disk encryption and other USB/Drive support.

To download it, same link again : https://www.virtualbox.org/wiki/Downloads

-To install it, open **Oracle VirtualBox** , then go to 'file' , then 'tools' , then 'Extension Pack Manager' and add your extension using the + button. Using 'CTRL+T' is the same.


## Step 2 : Installing your Virtual Machines

### 1.1 Downloading 

In order to setup our machines, we need to download their .iso disk and then mount them onto Virtual Box. 
First of all we download our .iso files : 
- For Ubuntu : https://www.ubuntu-fr.org/download/
- For Kali Linux : https://www.kali.org/get-kali/#kali-virtual-machines and choose the VirtualBox one







