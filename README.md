1.Download and install VMWare WorkStation 16
2.Download Ubuntu 20.04.3 disc image.
3.Configure Ubuntu in VMware Workstation.
4.Allocate the resources as follows -
     1.Memory - 8GB
     2.Disk Space - 100GB
     3.CPU - 8
5.Fork the Linux repository on github account
6.Clone the repository
7.Create cmpe283-1.c using touch cmpe283-1.c command
8.Modify the content as per as the requirement.
9.cd Linux
10.sudo apt-get install manpages-dev
11.Copied the config file using cp /boot/config-5.11.0-38-generic .config
12.Execute the following commands
make oldconfig
make prepare
make clean
make prepare
make -j 8 module
make -j 8
sudo make INSTALL_MOD_STRIP=1 modules_install
sudo make install
uname -a
sudo reboot
uname -a
make
sudo insmod cmpe283-1.ko
lsmod | grep cmpe283
Demsg


Issues faced during the execution -
Got an error while executing make oldconfig - Installed flex and bison libraries to resolve it
Got an error while executing make prepare - Installed  libelf-dev  and libncurses-dev to resolve all the package related issues.
Got an error while executing make -j <cpu num> - Changed the value of CONFIG_SYSTEM_TRUSTED_KEYS  and CONFIG_SYSTEM_REVOCATION_KEYS to null.
 Got an error while executing make -j <cpu num> -   Disabled  CONFIG_DEBUG_INFO BIT
