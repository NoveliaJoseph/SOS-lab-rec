SAMBA SHARE
Experiment: 2
Aim: Installation and configuration of Samba share.
Description:

SAMBA

One of the most common ways to network Ubuntu and Windows computers is to configure Samba as a File Server. This section covers setting up a Samba server to share files with Windows clients.
The server will be configured to share files with any client on the network without prompting for a password. If your environment requires stricter Access Controls see Share Access Control
Port No: 139
Package name: samba
Configuration file: /etc/samba/smb.conf.

Procedure:

To install Samba, we can run:
$sudo apt update
$sudo apt install samba
We can check if the installation was successful by running:
$whereis samba
Now that Samba is installed, we need to create a directory for it to share:
$mkdir /home/&lt;username&gt;/sambashare/
The command above creates a new folder samba share in our home directory which we will share later.The configuration file for Samba is located at
/etc/samba/smb.conf. To add the new directory as a share,we edit the file by running:
$sudo nano /etc/samba/smb.conf
At the bottom of the file, add the following lines:

[sambashare]
comment = Samba on Ubuntu
path = /home/username/sambashare read only = no
browsable = yes
Then press Ctrl-O to save and Ctrl-X to exit from the nano text editor.
Now that we have our new share configured, save it and restart Samba for it to take effect:
$sudo service smbd restart
Update the firewall rules to allow Samba traffic:
$sudo ufw allow samba

SETTING UP USER ACCOUNTS AND CONNECTING TO SHARE

Since Samba doesn’t use the system account password, we need to set up a Samba
password for our user account:
$sudo smbpasswd -a username

CONNECTING TO SHARE

On Ubuntu: Open up the default file manager and click Connect to Server then enter: Connecting to samba via smb://127.0.0.1/sambashare

Note: ip-address is the Samba server IP address and sambashare is the name of the
share. You’ll be prompted for your credentials. Enter them to connect!


Conclusion:

All the commands have been executed and the output has been obtained successfully.
