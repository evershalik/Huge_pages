# Huge_pages

**This repo will help you to add huge pager to your system**


Firstly check that does your system support huge pages or not by running the following command:
```
grep Huge /proc/meminfo
```
 If it shows any output it means your device supports huge pages.
 You will get some output like this:
 
![image](https://user-images.githubusercontent.com/98207888/204806320-32e689e2-363d-4ee7-93c0-a4ae368b8b9a.png)

Most likely, your huge page size will be configured to 2 MB, which is the standard on modern systems.

Now let's change our pages size to 2GB i.e 2MB*1024 (you can change it to any values).
In order to do so run the following command:
```
sudo sysctl -w vm.nr_hugepages=1024
```
To make these changes persistent so that it will stay even after reboot, you have to add a command to the file at this location.
`/etc/sysctl.conf`.
So, run command:
```
sudo vim /etc/sysctl.conf
```

And add this command  at last line manually to the file:
```
vm.nr_hugepages = 1024
```
After that save and exit the file.

Now reboot your system and check now using the same commands:
```
grep Huge /proc/meminfo
```

This time you will find some different values like this:

![image](https://user-images.githubusercontent.com/98207888/204807862-3b1cfd47-c18d-44b4-b8e2-f904113986dc.png)


Reference:
[Click here](https://wiki.debian.org/Hugepages)
