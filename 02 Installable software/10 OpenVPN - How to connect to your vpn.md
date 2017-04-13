OpenVPN - How to connect to your vpn
====================================

This software can be installed from the manager [Install Software](https://www.feralhosting.com/manager/).  
  
After OpenVPN has been set up on your server you will need to install an OpenVPN client on your own computer to use it.  
  

Windows
-------

  
Using the [OpenVPN Stable/Current](http://openvpn.net/index.php/open-source/downloads.html) is relatively easy on a Windows machine.  
  
After installing, you should connect to your server via SFTP (use an FTP/SFTP client such as Filezilla) and download the contents of  
  

    ~/private/vpn/

  
Full path will look something like:  
  

    /media/DiskID/home/username/private/vpn/

  
Copy the contents of this folder into:  
  

    C:/Program Files/OpenVPN/config/

  
(or the location where OpenVPN was installed, maybe `Program Files (x86)`).  
  
So after you have downloaded the files to your:  
  

    /config folder

  
You will see inside it:  
  
**1:** client.ovpn  
  
**2:** keys directory  
  
![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/Installable%20software/OpenVPN%20-%20How%20to%20connect%20to%20your%20vpn/keysdirectory.png)  
  
Now start the opengui as admin, once it has loaded you should be able to right click on the icon and Connect.  
  
![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/Installable%20software/OpenVPN%20-%20How%20to%20connect%20to%20your%20vpn/connect.png)  
  
**NOTE:** After some recent windows updates it seem you must run openvpn GUI as Admin. To check it is working after openvpn has connected and the icon is green check your IP in your default browser  
  
**NOTE:**  
  
On `some` Windows 7/8 systems, internet traffic is not properly routed through the VPN. In such a case the client.ovpn file must be edited, adding these lines at the end:  
  

    route-method exe
    route-delay
    route-metric 512
    route 0.0.0.0 0.0.0.0

  
**OS X & Snow Leopard**  
  
The networking stack of OS X has VPN support built-in, however a dedicated client offers better configuration and is easier. [Tunnelblick](http://www.tunnelblick.net/) is the best free client, however this is currently not working well in Snow Leopard. [Viscosity](http://www.viscosityvpn.com/index.html), which costs $9, has a much nicer GUI, better configuration, and fully supports both Leopard and Snow Leopard.  
  
You need to download the contents of `~/private/vpn/` to a secure location in your home directory. Then in Viscosity Preferences, simply "Import Connection" and use the client.ovpn file; Viscosity will import all the needed data. You can then delete the vpn directory you downloaded as Viscosity stores the data in its own Library location.  
  
Update 2015-04-11 - The ovpn file doesn't setup the TLS-Auth shared key properly. In Viscosity's Authentication settings, under Extra &gt; Tls-Auth set the key to tls-auth.key and the direction to 1.  
  
![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/Installable%20software/OpenVPN%20-%20How%20to%20connect%20to%20your%20vpn/osx1.png)  
  

iOS
---

  
**1:** Download [OpenVPN Connect](https://itunes.apple.com/us/app/openvpn-connect/id590379981?mt=8) from the app store.  It's a free download.  
  
**2:** Download the contents of ~/private/vpn to the machine you sync your device with.  
  
**3:** Open iTunes on your PC.  Go to your device's 'apps' tab.  Scroll down until you see file sharing and then select OpenVPN Connect in the list of apps.  
  
**4:** Add client.ovpn AND the files inside the 'keys' folder (rather than the folder itself) to OpenVPN Connect's folder.  
  
**5:** Launch OpenVPN Connect on your iOS device.  It will prompt you to add a new connection; press the plus sign.  
  
**6:** Enjoy your new VPN.  
  

Android 4.0 +
-------------

  
Use this FAQ:  
  
[OpenVPN - Connect on Android 4.0 and up - using OpenVPN Connect](https://www.feralhosting.com/faq/view?question=220)  
  

Linux
-----

  
Linux generally comes with clients built-in to their network managers.  
  
`Note: the file keys/<username>.key should be secret at all times.` This includes never transferring it over an insecure connection or moving it to a place where you do not have complete control over. For this reason you should always use SFTP to transfer the file and not FTP. If there was a mistake made during this process a new key can be generated by [installing through the account manager](https://www.feralhosting.com/manager/software-install) again.  
  

Ubuntu 10.04
------------

  
First, make sure you have the keys folder and the client.ovpn file somewhere on your hard drive. They should have been downloaded from the /private/vpn/ folder of your server via SFTP (winscp works fine in wine).  
  
Open up the Ubuntu Software centre from the applications menu. Search for "network-manager-openvpn".  
  
![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/Installable%20software/OpenVPN%20-%20How%20to%20connect%20to%20your%20vpn/ubuntu1.png)  
  
Choose the "Gnome" version which is highlighted above. You should see an install button where the remove button is. Click it. Openvpn will now be installed.  
  
Next, right-click on the network icon in the upper-right of the screen, and select "Edit Connections".  
  
![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/Installable%20software/OpenVPN%20-%20How%20to%20connect%20to%20your%20vpn/ubuntu2.png)  
  
Navigate to the VPN tab and click "import".  
  
![](https://raw.github.com/feralhosting/feralfilehosting/master/Feral%20Wiki/Installable%20software/OpenVPN%20-%20How%20to%20connect%20to%20your%20vpn/ubuntu3.png)  
  
Select your client.ovpn file that you downloaded earlier using SFTP. Make sure the keys folder and the client.ovpn file are in the same directory to make this a little easier.  
  
On this screen, everything should be filled in already. At the top you can change the name of the VPN connection and choose whether you want to connect to it automatically. Click apply, and close the "network connections" window.  
  
Now, your OpenVPN connection should be ready to go. Left-click on the network icon, select VPN connections, and then click the name of the one you just created. Within a few seconds you will notice a lock on your connection icon, signalling you are connected.  
  
Note: Rebooting your PC may also be necessary, so if OpenVPN fails to connect try a reboot.  
  

Confirmation of an Active VPN Connection
----------------------------------------

  
After this is set up and the OpenVPN GUI is running, you should check that your IP address appears the same as the server to websites you visit: go to <http://whatismyipaddress.com/> and make sure the server IP provided is reported back to you. If it isn't and you appear to be connected, something has gone wrong and your communications are not being encrypted.  
  

ubuntu 11.10 OpenVPN connection instruction (likely to work on 10.04, 10.10, 11.04
----------------------------------------------------------------------------------

  
**1:** Install openvpn software at [OpenVPN](https://www.feralhosting.com/manager/slot/install?service=20036)  
and wait a few minutes  
  
**2:** connect to account via scp or sftp and navigate to the private directory. Look for the file called client.ovpn and download it.  
Also in the vpn directory, there is another directory called keys that needs te be downloaded. Upon downloading locally, be certain all 6 files are in the same directory on your computer.   
Example path to files on feralhosting: /media/sdb1/home/YOURUSERNAME/private/vpn  
  
**3:** From here you will configure the vpn connection using the network manager in ubuntu. Click on configure VPN followed by import.  
  
**4:** Choose the client.ovpn to import which will select in the type (certificate).  
  
**5:** Name the connection and ensure the gateway is your feralhosting server. ex server.feralhosting.com  
  
**6:** Click on the file icon to choose you user certificate (ends in .crt) Moving on, choose the CA certificate called ca.crt and ending with the private key such as username.key.  
  
**7:** Locate the advanced icon in the lower right corner and click it.  
  
**8:** Select the tab "TLS Authentication".  
  
**9:** Check the box "Use additional TLS authentication".  
  
**10:** Choose the key file from the same directory as all the other files you have used, it will be called tls-auth.key.  
  
**11:** Save & connect.  
  
**12:** open a terminal and type curl ifconfig.me to see what your IP address is.  
  
If you cannot connect, open a terminal up and type:  
  

    tail -f /var/log/syslog

  
This will monitor the NetworkManager as you try and connect to the VPN. Review and google the answers to best determine what is preventing the connection.  
  

Selective VPN routing
---------------------

  
By default, the OpenVPN server will advertise itself as the default gateway for your client. If you don't want this to happen, add the following to the end of your OpenVPN client configuration file (client.ovpn):  

    route-noexec

  
  
After this, you can use routing commands to configure the desired routes. The method of doing this will vary based on your operating system, but here are some examples for a Linux based system. In each of these examples, it is assumed that your VPN network interface is named tun0:  

    # Add a route for all hosts on the network 123.45.67.0/24 via the VPN:
    route add -net 123.45.67.0/24 dev tun0
    # Add a route to 123.45.67.89 via the VPN:
    route add -host 123.45.67.89 dev tun0

  
