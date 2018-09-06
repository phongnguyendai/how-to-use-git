# Overview
SSH is a secure protocol for communication between machines and 
it is also one of the most useful tool that users SSH to enable
mounting of a remote files system on a local machine
# Installaion and Setup
open command line and type:
`sudo gpasswd -a $USER fuse`
Alternatively, or you can use GNOME by executing as the following link:
`System -> Administration -> Users and Groups -> (your user) -> Properties -> User`
Privileges, then tick the following option:
# Command-line Usage
To mount the remote directory, we will run the simply command SSH as follows:
`mkdir ~/far_project` # create a local mount directory
`sshfs -o idmap=user $USER@far:/projects ~/far_projects` #projects is the 
remote directory

To unmount:
`fusermount -u ~/far_projects`
`To add it to your /etc/fstab`
`sshfs#$USER@far:/projects /home/$USER/far_projects fuse defaults,idmap=user 0 0`
Note: that you have to change $USER to your login name when editing fstab, but it is not necessary when typing commands (the shell does it for you in that case).
The idmap=user option ensures that files owned by the remote user are owned by the local user.
# Keep Alive
Your ssh session will automatically log out if it is idle
. To keep the connection active (alive) add this to:\
`~/.ssh/config` or to `/etc/ssh/ssh_config` on the client.
ServerAliveInterval 5
This will send a "keep alive" signal to the server every 5 seconds. You can usually increase this interval, and I use 120.
