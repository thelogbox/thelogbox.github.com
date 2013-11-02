---
layout: linux

title: File Sharing between OSX and Linux

description: How to transfer files between Linux and Mac

tags:
- File
- Sharing

categories:
- Linux

---



Plenty of ways to share files between Linux and Mac, after all, they are brethrens because of their UNIX nature -- I would have said lineage but that may be contestable by the purists. After all, I am not an expert on UNIX history.

History and purity aside, some of the ways of sharing files between these two systems are;

+ **CIFS or SMB (Samba)**, Common Internet File System or Server Message Block, respectively. The Mac comes with smb out of the box, but the Linux side of the fence is not so predictable. It depends on what Linux distribution you have used and the installation route that you took. You may have to install some software on the Linux side
+ **SCP or SFTP**. Again, the Mac comes with the SSH swiss knife out of the box. On Linux, you may have to install the SSH software as an add-on
+. The very reliable *FTP*
+ **RSync**. A quick way to bring two file systems into sync (as the name implies). RSync is a bit different from the others mentioned here because you mostly employ this system on situations where you need one file system or folder to be perfect clone or mirror of another
+ **NFS**, short for Network File Share -- There are plenty of Linux distributions to use but for the purpose of this guide, Debian has been chosen (which means this installation is very similar if you are using Ubuntu or any of its derivatives)
+ **AFP** Apple File Protocol
+ And of course, probably the easiest of all **DropBox**


## 1. Use Linux as the Samba (SMB) server 

You need to be a bit comfortable working with the Linux terminal in order to perform most of these exercises. While there are methods perform these administrative tasks using some GUI tools (like SWAT), it much more straightforward to do them in the Terminal). Any terminal should be okay like xTerm, rTerm, Terminator or Gnome-Terminal. In the sections ahead, I will no longer mention that the highlighted commands should be performed on the Terminal because all of them will be.

### Preparing what we need to get Samba up and running

**Get Samba from the repositories1**

    $ sudo apt-get install samba smbfs

**Edit the Samba configuration file**, it's found under */etc/samba/smb.conf*. A bit of a tip, it's easier to start with a clean slate of smb.conf than to edit the original configuration file -- that way, if you mess the configuration, you can always go back to a fresh, untouched config file.

    $ cd /etc/samba
    $ sudo mv smb.conf smb.conf.original
    $ sudo touch smb.conf
    $ sudo nano smb.conf

The *mv(move)* command renames smb.conf to smb.conf.original. The *touch* command creates a file called smb.conf -- a blank one; And nano, opens smb.conf for editing, you don't really have to use nano if you are comfortable with another text editor, just use what you like.


Starting with a blank samba configuration file is both intimidating (if you are not used to it) and liberating (if you have done this quite a couple of times). A very basic file share in samba needs the following lines



    security=user
    username map=/etc/samba/smbusers

    [homes]
    comment=Home Directories
    browseable=yes
    writable=yes
    valid=%S ; so that only the defined users can view it


**security=user** means that samba will allow access only to the users that you (will) define in */etc/samba/smbusers*

**username map=/etc/samba/smbusers** means that a samba user defined in the file *smbusers* also have a shell account (the user can login to your linux box and has an entry on the /home/ folder. If you need to check if the user(s) you are defining has a shell account, you can use the command **$ sudo id NameOfUser**

The lines after '[home]' defines which folders Windows users can see, access, and write to, the rest is self explanatory.

**Save the smb.conf**. If you use the nano editor *CTRL-O then CTRL-X*, ctrl-O saves the file in nano, ctrl-X exits nano.

**Create the Linux shell account for your users**

    $ sudo adduser firstuser

You will be asked to input a password for firstuser, and a couple more more information that you might have enter. After the creation dialog has finished, make sure that the user has been successfully created by typing

    $ sudo id firstuser

If you don't see "no such user", you're in good shape. Just repeat step #5 for every shell account you want to create, say "seconduser".

**Create and populate the smbusers file**

    $ cd /etc/samba
    $ sudo touch smbusers
    $ sudo nano smbusers


**Map the Linux shell account to the Samba account**, this is the content of the */etc/samba/smbusers* file


    firstuser=firstuser
    seconduser=seconduser


**Set the samba password for the user**

A user's password in samba is not the same as the user's shell account password (the password to login to the Linux box), Both passwords can be identical though if you choose to, but they don't have to be.


    $ sudo smbpasswd -a firstuser

You will be asked for a password -- twice! The -a option in smbpasswd means that the firstuser password will be added to /etc/samba/smbpasswd file. The shell accoun for *firstuser* should already exist, otherwise the smbpasswd will fail.

Reboot; **$ sudo reboot** should do it.

In your Mac, you should be able to see the name of Samba server in your *Finder*. If you are using Windows, the file server should be visible in the *Network* places.

Samba will challenge you for your username and password, what it is asking for is the username and password entry in the */etc/samba/smbusers* and not your shell account username/password -- This is why it is a good idea to keep the shell account credentials and smbusers credentials identical.


##2. SCP (Secure copy) and SFTP (Secure FTP) 

**Install SSH on the Linux end** if it doesn't have it yet.  

    $ sudo apt-get update
    $ sudo apt-get upgrade
    $ sudo apt-get install ssh openssh-server

To copy one file from the Mac to the Linux server

    $ scp path/to/file linuxUserName@LinuxServer:/path/to/linux/destination/FILENAME-TO-COPY

Replace *path/to/file* with the folder path and file to copy. This is why it is a good idea to be verbose when doing this kind of stuff. You should *cd* first to the directory where the source file (file to be copied) is before performing the above command.

Replace *linuxUsername* with your shell account in Linux. The *LinuxServer* is either the name or IP address of your Linux server

**SFTP** is much easier to do from a Mac. Get either [CyberDuck][cid] or [FileZilla][fid] for your Mac. Open a connection, use your linux username on the *username* textfield. Use the *linuxName* or *IpAddress* on the hostname textfield **AND** don't forget to enter **22** on the port number -- That is what makes SFTP different from regular FTP. Regular FTP uses *port # 21* while SFTP ues *port number 22* 

The rest of the file copying/moving is the same as that of regular FTP.

[cid]: http://cyberduck.sh
[fid]: http://filezilla-project.org

##3. RSync 

RSync is a bit different from the rest of file sharing methods discussed here. The other file sharing methods does not require nor result in two file locations having exactly the same content . RSync is actually inteded for mirroring purposes, and because of that characteristic, it is more akin to software like [amanda][amandaid], [drbd][drbdid] and [lsync][lid] to name a few -- of course there are more. 

### Get a basic RSync running on a Linux server 

**Install rsync**  

    $ sudo apt-get install rsync

**Create the conf file and configure rsync** 


    $ sudo touch /etc/rsync/rsyncd.conf

    #contents of file rsyncd,conf

    max connections = 2
    log file = /var/log/rsync.log
    time = 300
    
    [mine]
    
    comment = Folder I would like to sync
    path = /path/to/folder/tobe/synced
    read only = yes
    uid = nogroup
    gid = nogroup
    auth users = mine
    secretst file = /etc/rsyncd.secrets
    hosts allow = 192.168.0.0/24 

-- INCOMPLETE GUIDE -- need to finish the rsync instructions


[amandaid]: http://www.amanda.org
[drbdid]: http://www.drbd.org
[lid]:http://code.google.com/p/lsyncd/

##4. Use Linux as an NFS server


1. Get some packages from the repositories. You can do this either via Synaptic (if you are using a desktop software like Gnome) or, better yet, from a Linux Terminal window, you can

<pre><code>
$ sudo apt get install nfs-kernel-server nfs-common portmap sysv-rc-conf
</code></pre>

Only the first three software is all we need for NFS but the **sysv-rc-conf** is handy utility so that you can start/stop/restart any service on the Linux server. **sysv-rc-conf**  has an ncurses user interface which let you manage the state of services by just pointing to the service using the arrow keys, then pressing the plus sign (+) to start a service and the minus (-) sign to stop a service

2. After getting the packages, you will need to edit */etc/exports* file and add some lines so that you can expose the folders that you would like share using NFS

<pre><code>
/home (rw,sync,no_subtree_check,insecure)
/mnt/foldertoshare (rw,sync,no_subtree_check,insecure)
</code></pre>

3. Replace /home and /mnt/foldertoshare with your own folders that you'd like to share. I had to include the 'insecure' option in the exports declaration because OSX wouldn't let me mount without that option. There are other types of declaration you can do in the exports file, but it's beyond the scope of this post--I'll put some more time on this one, then I'll redo this post to include the other options for NFS exports file.

4. After editing */etc/exports*, **RESTART** the nfs server, you can do that 2 ways. First is by

<pre><code>
$ sudo /etc/init.d/nfs-kernel-server restart
</code></pre>

The second is to invoke sysv-rc-conf from the command line, then use your arrow keys to find nfs-kernel-server, then press '-' sign to stop, then press '+' sign to start.


### How to use NFS using Mac as the client and Linux as the server

There is a GUI way to mount NFS drives in Mac, but I suggest you use **Terminal.app**. Access Terminal.app from *Applications-->Utilities* folder then type the following


    $ mkdir ~/mymount
    $ cd ~
    $ sudo mount servername:/mnt/badass ~/mymount


The first command createas a local folder under the user directory (/User/yourname). The second command switches to that directory. The third command mounts the network file system you have defined in the Linux server as local folder in OSX.

All the contents of the shared files in your NFS server should now be accessible within the mymount folder, just cd to **~/mymount** and use it as if the file is local to your Mac. You can even view this network folder in *Finder* and it will appear as a regular folder.
