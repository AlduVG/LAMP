# Linux + Apache + MYSQL + PHP

Welcome! In this project, I'll guide you through the process of setting up a LAMP stack using Virtual Box.

**Prerequisites:**

Latest Ubuntu version (Ubuntu 22.04.1 was used for this project).

Any virtualization tool (Oracle VM Virtual Box was used in this project).

Putty.

## Setting up Virtual Box and Ubuntu install.
I've allocated **2 GB of RAM** and **20 GB of disk space** to our virtual machine to ensure it has enough resources to run our LAMP server efficiently. A bridged connection will allow the virtual machine to communicate with the local network as if it were an independent physical machine.
Now that we have our configuration set, let's proceed to install the operating system on our virtual machine. In this case, I'll be using Ubuntu, a widely used Linux distribution that is compatible with our LAMP stack.

Let's start up VirtualBox and create a new virtual machine.
Download the Ubuntu ISO image and select it as the installation medium.
Follow the standard Ubuntu installation instructions.

## Static IP address and SSH.
We are going to assign a static IP address to our virtual machine. This will make it easier to identify the host on the network, as we will always know the assigned IP address. To begin, we need to navigate to the network configuration directory. We will use the following command:

**cd /etc/netplan/**

Once in the network configuration directory, we will use the ls command to list the contents of the folder. In the image I'm sharing, you can observe the presence of the *"01-network-manager-all.yaml"* file. We will edit this file using the following command:

**sudo nano 01-network-manager-all.yaml**
<p align="center">
  
  ![netwoorkManager](https://github.com/AlduVG/LAMP/assets/131760637/eaab4ba2-723f-4e37-a10e-6294ace0d246)</p> 
  
You can also use the following approach if you prefer to move directly to the folder and then edit the file:

**sudo nano /etc/netplan/01-network-manager-all.yaml**

Next, we will add the following information to the file:

    ethernets:
  
      enp0s3:
    
          addresses: [192.168.1.150/24]
        
          gateway4: 192.168.1.1

          nameservers:
        
              addresses: [8.8.8.8, 8.8.4.4]
            
<p align="center">
  
  ![networkmanager](https://github.com/AlduVG/LAMP/assets/131760637/bb927f21-bc6d-4367-8783-66c834952456)</p>
  
To determine the assigned interface on our virtual machine, we can use the **ifconfig** command. This information will be crucial when configuring the *"01-network-manager-all.yaml"* file. In my case, I will use the IP address **192.168.1.150/24**.
 <p align="center">   
   
  ![ifconfig](https://github.com/AlduVG/LAMP/assets/131760637/2e3cfa16-5dea-4215-a7ec-a8a0e1fe7a60)</p>   

I obtained the gateway from my Windows host using the **ipconfig** command. For DNS servers, we will use Google's servers: **8.8.8.8** and **8.8.4.4**.
Once we have completed this configuration, we can use the **ping** command to confirm connectivity. In my case, I will run the ping command from the Windows host to my virtual machine, just to verify that the connection has been established correctly.
<p align="center">
  
  ![ping](https://github.com/AlduVG/LAMP/assets/131760637/4ceec0ba-97b8-42b0-9b7f-d9175bdd78b8)</p>
  
<p align="center">
  
  ![putty](https://github.com/AlduVG/LAMP/assets/131760637/a34ee77b-0820-4aec-bebd-8edbb2fed872)</p>    
  
<p align="center">
  
  ![connectingtoourhost](https://github.com/AlduVG/LAMP/assets/131760637/48483b35-fd87-4cd9-9bab-869f7778a926)</p>
If no issues arise, we will be ready to use **SSH** to remotely administer our virtual machine.

**Note:** Remember to adjust the values according to your network configuration and host operating system.

## Installing Apache.
Now, let's install **Apache** on our Ubuntu OS. Since I'm connected from my host to the virtual machine, I'll install **Apache** with the following command:


**sudo apt install apache2**
<p align="center">
  
  ![apacheinstall](https://github.com/AlduVG/LAMP/assets/131760637/09234a30-243f-4421-90a1-46f7ee325653)
</p>

Once it's installed, we'll confirm the status of the service using this command:

**sudo systemctl status apache2**

<p align="center">
  
  ![ApacheCheck](https://github.com/AlduVG/LAMP/assets/131760637/5ad86d2d-a376-4b12-9f94-ca5e2515fdf6)
</p>

Next, we'll return to our virtual machine and open our web browser. We'll enter the following URLs to double-check that Apache is working:

*http://yourserverip*

*http://localhost*

<p align="center"> 
  
  ![checarapache](https://github.com/AlduVG/LAMP/assets/131760637/4215329c-d7af-499a-a013-636d9746e668)</p>

## Installing MySQL.
  <p align="center">
    
  ![InstallingMySQL](https://github.com/AlduVG/LAMP/assets/131760637/2c8c3dce-b0e8-4593-82bc-721e178fc14a)</p>
 <p align="center">
  
  ![StatusCheckMySQL](https://github.com/AlduVG/LAMP/assets/131760637/aca7fddb-3d40-4c94-b472-d08f4ce5de7a)</p> 
## Installing PHP.

<p align="center">
  
  ![PHPInstall](https://github.com/AlduVG/LAMP/assets/131760637/fe9f0ee0-c71c-4888-89c5-42cdfea61ff9)</p>
    <p align="center">
  
  ![info PHP](https://github.com/AlduVG/LAMP/assets/131760637/6e535b1c-9360-46fa-abdd-ae2b92288c92)</p>
  <p align="center">
  
  ![PHPinfoBrowser](https://github.com/AlduVG/LAMP/assets/131760637/195a1aef-53e9-4c88-89d0-846d578d427a)</p>
  <p align="center">
  
  ![rmPHPinfo](https://github.com/AlduVG/LAMP/assets/131760637/a1381cad-83d0-43c9-8c91-8fc9451c9c10)</p>
## Installing PHPmyadmin.
<p align="center">
  
  ![PHPmyadmininstall1](https://github.com/AlduVG/LAMP/assets/131760637/5e0d8d39-a1f1-4651-8f76-ba801512e49e)</p>
<p align="center"> 
  
  ![Apache conf2Edit](https://github.com/AlduVG/LAMP/assets/131760637/672e3b72-7f02-4280-9bc2-67f846ec27ae)
</p>  
<p align="center">
  
  ![phpmyadmin](https://github.com/AlduVG/LAMP/assets/131760637/cdd5fd49-d544-4ca6-bfbf-9d073037187f)</p>













