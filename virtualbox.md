## VirtualBox Won't Start (Failed to acquire the VirtualBox COM object)

Steps to restore a copy

1. Ensure VirtualBox Manager is not running.
1. Navigate to ~/.config/VirtualBox/
1. Rename ~/.config/VirtualBox/VirtualBox.xml to something like ~/.config/VirtualBox/VirtualBox.xml-original
1. Rename the backup ~/.config/VirtualBox/VirtualBox.xml-prev to ~/.config/VirtualBox/VirtualBox.xml
1. Start VirtualBox Manager. This is a copy of the state of the last VirtualBox Manager startup, and [this solved my problem, so] hopefully [it] resolves your situation [as well].

For details check the original [post](https://superuser.com/questions/1588519/virtualbox-wont-start-failed-to-acquire-the-virtualbox-com-object).


## Create a shared folder

Check this link for the details: 
- https://net2.com/how-to-share-folders-between-your-ubuntu-virtualbox-and-your-host-machine/

After creating a shared folder with `auto mount` option, you can see the shared folder as new drive (mount point can be found in `/media`) but cannot be accessed.

In order to access the shared folders, we need to add the user to a group called `vboxsf` (there are users and groups). Open up your terminal and run the command below :

```
$ sudo adduser <username> vboxsf
```

Now enter the command :

```
sudo reboot
```

Now we can create or copy your resources in the shared folder, and all these will be aviable in host machine.

I use a git in VM, but don't have any remote git server for my confidential projects. However, I have onedrive in Windows host and i use shared folder approach to keep the VM data backup in Onedrive as a quick soultions. You might think that I could use github (etc.) as remote git server, but i cannot use that for specific reason.



