FTP
Experiment : 6
Aim : To create and configure FTP Server
Description :
FTP Server

File Transfer Protocol (FTP) is a TCP protocol for downloading files between computers. In the past, it has also been used for uploading but, as that method does not use encryption, user credentials as well as data transferred in the clear and are easily intercepted. So if you are here looking for a way to upload and download files securely,

FTP works on a client/server model. The server component is called an FTP daemon. It continuously listens for FTP requests from remote clients. When a request is received, it manages the login and sets up the connection. For the duration of the session it executes any of commands sent by the FTP client
Port No: 21
Package name: vsftpd
Configuration file: /etc/vsftpd.conf

Procedure:
Install the vsftpd - FTP Server Installation in the ubuntu operating system
$sudo apt install vsftpd
By default vsftpd is not configured to allow anonymous download. If you wish to enable anonymous download edit /etc/vsftpd.conf by changing:
$anonymous_enable=YES
During installation a ftp user is created with a home directory of /srv/ftp. This is the default FTP directory.
If you wish to change this location, to /srv/files/ftp for example, simply create a directory in another location and change the ftp user’s home directory:
$sudo mkdir -p /srv/files/ftp
$sudo usermod -d /srv/files/ftp ftp
After making the change restart vsftpd:
$ sudo service vsftpd restart

User Authenticated FTP Configuration

By default vsftpd is configured to authenticate system users and allow them to download files. If you want users to be able to upload files, edit /etc/vsftpd.conf
$write_enable=YES


Now restart vsftpd:
$ sudo service vsftpd restart


Securing FTP
There are options in /etc/vsftpd.conf to help make vsftpd more secure.
$chroot_local_user=YES
$chroot_list_enable=YES
$chroot_list_file=/etc/vsftpd.chroot_list


After uncommenting the above options, create a /etc/vsftpd.chroot_list containing a list of users one per line.

Then restart vsftpd:
$sudo service vsftpd restart


To configure FTPS, edit /etc/vsftpd.conf and at the bottom add:
$ssl_enable=YES


Then check the vsftpd status
$sudo service vsftpd status


Now connect to ftp by the command
$ftp -p 192.168.234.128


Now install filezilla in ubuntu and open the filezilla and specify the ip address and port number of the ftp server then click connect
Conclusion:

All the commands have been executed and the output has been obtained successfully
