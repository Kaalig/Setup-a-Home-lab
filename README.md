# Set up a Home lab

A simple write up where i'm setting up a Home Lab using a type II hypervisor, a *Virtual Machine* in our case. For this project we will setup an offensive machine and a defensive machine, both linux distribution, and we will simulate an attack between two machines and a way to mitigate it. 

I will go with the easiest to use and most known offensive linux distribution : **Kali Linux**. For our defensive machine, I will go with the lastest version of **Ubuntu**, as I am emulating a normal user account surfing on the internet. 

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
*Note : I tend to always upgrade my distribution before installing something on Linux in order to not have any weird problems. It's better to prevent than to repair !*

### 1.2 Installing extension package

Extension package of VirtualBox is not a necessity but it gives some interesting feature like USB 2.0/3.00 , Disk encryption and other USB/Drive support.

To download it, same link again : https://www.virtualbox.org/wiki/Downloads

-To install it, open **Oracle VirtualBox** , then go to '**file**' , then '**tools**' , then '**Extension Pack Manager**' and add your extension using the + button. Using '**CTRL+T**' will do the same result.


## Step 2 : Creating your Virtual Machines

### 1.1 Downloading 

In order to setup our machines, we need to download their .iso disk and then mount them onto Virtual Box. 
First of all we download our .iso files : 
- For Ubuntu : https://www.ubuntu-fr.org/download/ (5 GB ~)
- For Kali Linux : https://www.kali.org/get-kali/#kali-virtual-machines (4 GB ~) and choose the VirtualBox one

### 1.2 Installing our .iso

*Note : Order of creation does not matter. You can create your Kali VM first if you want.*

- After that we open VirtualBox and we click on "**+ ADD**" to add our machines. Name them whatever you want them to be name. 
- Choose the type (**Linux** for both) and the version (**Ubuntu** for Ubuntu obviously / **Debian or Ubuntu** for Kali)
- Allocate memory to both VMs. 4GB or more is recommended. If your computer can't manage to give 4GB+ to a VM, just put 2Gb but be aware that it will be **really slow** and you should take your time during every manipulation.
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

- Go to **Config** then **Network** . If we want to have a direct access to our home network, we use the **bridged adapter** . If we want a private network running, we use **NAT** . For our project  **NAT** is more interesting. Now problem is, we still don't have a NAT network so let's make one.
- Go to **files** then **tools** and select **Network Manager** and create a new network. Ipv4 should look like that : **10.0.2.0/24**

Last step is to change again your configuration per machine. Instead of using just NAT in our network settings, we will use ***NAT Network*** and select the network name to make it work.


## Step 4 : Install and configure Tools

At this point, your machines are configured and installed, ready to be used for the first time.

When you load Ubuntu for the first time, we should first of all update the OS just in case, and then get some essentials tools that Ubuntu user generally have. Here's the code :
```
sudo apt update && sudo apt upgrade -y
sudo apt install -y build-essential git curl wget

```
Note : We invoke sudo to have the administrator right and we update (apt update) our machine to te latest version and we upgrade all the packages with have with apt upgrade. Flag -y is for answering yes to every prompt we could have after typing this command.


For Kali Linux, since it is an OS that comes with many features and most of them are really good, it is not necessary to install more tools yet. Simply update and upgrade again like we did earlier.


## Step 5 : Simulate a network Attack & Defense

At this step, we will use an offensive tool in Kali Linux in order to gain information on our Ubuntu victim machine which is called **nmap** . This powerful tool will give us some information about what TCP port are open, and much more depending what flag you use. For now we will only launch a basic scan on the victim :

```
nmap -A 10.0.3.72 # Replace IP with your Ubuntu IP address
```

That should return some valuable information. 

Now let's go back to our Ubuntu machine. We will use a method that blocks every signal coming from our Kali IP address using a Firewall named UFW (Uncomplicated Firewall). 
Deploy Ubuntu and then do the following :
```
sudo apt install ufw
sudo ufw enable
sudo ufw deny from 10.0.3.72 # Replace with your Kali IP Address
sudo ufw status
```
We have installed it, enabled, deny every incoming packets that comes from this specific address and we checked if it commit.

However if we want to just monitor what our Kali Linux machine do from our Ubuntu's perspective, we will do something completely different. In this case it is interesting to see what is going on but you should never do it in real conditions :

```
sudo ufw enable
sudo ufw allow ssh
sudo ufw allow from 10.0.3.72 # Replace with Kali IP Address
sudo ufw status
```

Then on Ubuntu still, you will want to use **Wireshark** to analyze the network and capture the traffic :

```
sudo apt install wireshark
sudo wireshark
```

You will then see what is going on. Obviously what you see is out of this Walkthrought but it is still interesting to see what is going during during  an attack.

## Conclusion

We have successfully set up a home lab with multiple machines ready to operate and we connected them to our network. We also configurate our machines to not have any problems. Lastly we simulate a theoretical attack and their consequences but also a way to mitigate it.

Thanks for reading till the end. Hope it helped you in some ways. 
Bless you.



