## VirtualBox Won't Start (Failed to acquire the VirtualBox COM object)

Steps to restore a copy

1. Ensure VirtualBox Manager is not running.
1. Navigate to ~/.config/VirtualBox/
1. Rename ~/.config/VirtualBox/VirtualBox.xml to something like ~/.config/VirtualBox/VirtualBox.xml-original
1. Rename the backup ~/.config/VirtualBox/VirtualBox.xml-prev to ~/.config/VirtualBox/VirtualBox.xml
1. Start VirtualBox Manager. This is a copy of the state of the last VirtualBox Manager startup, and [this solved my problem, so] hopefully [it] resolves your situation [as well].

For details check the original [post](https://superuser.com/questions/1588519/virtualbox-wont-start-failed-to-acquire-the-virtualbox-com-object).
