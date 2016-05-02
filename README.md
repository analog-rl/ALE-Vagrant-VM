# ALE-Vagrant-VM
A ubuntu-based provisioning to deploy the Arcade Learning Environment with VirtualBox + Vagrant with all dependencies
# Currently using ale 0.5.1

Steps to create:
- Install VirtualBox: https://www.virtualbox.org/wiki/Downloads
- Install Vagrant https://www.vagrantup.com/downloads.html
- Create an env variable named ALE_ROOT that will point to the Arcade Learning Environment root. Example: 
```echo 'export ALE_ROOT=/Users/myusername/ALE-Vagrant-VM/Arcade-Learning-Environment' >> ~/.bash_profile ```
- source bash_profile for the change to take effect immediately: ```source ~/.bash_profile```
  
- ```vagrant up``` will start the provisioning (it might run a little long the first time as it has to download the ubuntu box image from Atlas (one-time process)
- once complete, you can get to the box by running ```vagrant ssh```

NOTE: The repo does not have any ROMs available, they are easy to find <a href="http://www.atariage.com/system_items.html?SystemID=2600&ItemTypeID=ROM">HERE</a> and otter places scattered around.  I ran a test of the setup by running the example script from the VM:
- ```vagrant up```
- ```vagrant ssh```
- ```cd ~/arcade_env/doc/examples```
Note: You will need to add roms to the Arcade Learning Environment ROMs folder.
- ```python python_example.py ~/arcade_env/rom/Breakout.bin``` 
