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


## Step 2 : Creating your Virtual Machines

### 1.1 Downloading 

In order to setup our machines, we need to download their .iso disk and then mount them onto Virtual Box. 
First of all we download our .iso files : 
- For Ubuntu : https://www.ubuntu-fr.org/download/ (5 GB ~)
- For Kali Linux : https://www.kali.org/get-kali/#kali-virtual-machines (4 GB ~) and choose the VirtualBox one

### 1.2 Installing our .iso

Note : Order of creation does not matter. You can create your Kali VM first if you want.

- After that we open VirtualBox and we click on "+ ADD" to add our machines. Name them whatever you want them to be name. 
- Choose the type (Linux for both) and the version (Ubuntu for Ubuntu obviously / Debian or Ubuntu for Kali)
- Allocate memory to both VMs. 4GB or more is recommended. If your computer can't manage to give 4GB+ to a VM, just put 2Gb but be aware that it will be really slow and you should take your time during every manipulation.
- Create a Hard disk space of 20 Gb or more if possible. 15Gb if not.



### 1.3 Installing OS

Start your VM and selection your ISO file as the startup disk. Then you will simply follow the installation instructions, which can take some times so don't be mad if it is not done in 5 minutes.

Instructions :
- It is different for others distributions but in the context of Kali and Ubuntu, follow the prompt (so the GRAPHICAL interface) to setup your language, keyboard and such.
- Partition the disk using the default option
- Create a user account and set your password
- Complete Installation and then reboot

## Step 3 : Configurate our network

We need to configure our network in order to fully utilize our VMs.

- Go to **Config** then **Network** . If we want to have a direct access to our home network, we use the **bridged adapter** . If we want a private network running, we use **NAT** . For our project  **NAT** is more interesting.












