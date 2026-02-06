# Common Linux terminal commands
## How to create a folder in linux terminal
    
    mkdir folder_name
    output -> a folder with given foldername will be created in the present directory

## How to delete an empty folder
    
    rmdir folder_name
    output -> a folder with given name will be deleted from the current directory

## How to delete an non-empty folder
    
    rm -r folder_name
    output -> a folder with given name will be deleted from the current directory

## How to list the files present in any folder

    ls components/hailo

## How to display the content present in any text file

    cat /boot/firmware/config.txt

## How to edit the content present in any text file

    nano /boot/firmware/config.txt

## If any command needs permission then run that command with sudo prefix

## To know about CPU 
    
    lscpu
    output -> CPU details

## To terminate the current terminal program
    
    ctrl + c
    output -> the program is terminated and we can start with any new instruction

## To update the package list in our system without installing or upgrading anything
    
    sudo apt update

## To just upgrade the installed packages without installing or removing anything
    
    sudo apt upgrade

## To install new packages, remove unnecessary packages and also update all dependencies
    
    sudo apt full-upgrade

## We can also combine above commands together as
    
    sudo apt update \&\& sudo apt full-upgrade

## To display the system performance
    
    htop

## To print something

    echo "what you want to print"
    echo "sameer"
    output -> sameer

## To list files and folders inside a folder

    ls (folder path)
    ls /sys/class/thermal/ 
    output -> different thermal zones that can be read by linux kernel

## To read the text written in a file

    cat (file path)
    cat /sys/class/thermal/thermal_zone0/temp 
    output -> the current CPU temperature

## To print something as well as run some command

    echo "what you want to print $(what you want to run as an inline command)"
    echo "CPU temperature: $(cat /sys/class/thermal/thermal_zone0/temp)"
    output -> CPU temperature reading in milidegrees

## To perform some operation on the read text

    echo "what you read as input | awk '{what you want to do on each field of each line of input}'"
    echo "CPU temperature: $(cat /sys/class/thermal/thermal_zone0/temp | awk '{print $1/1000}')"
    output -> CPU temperature in milidegrees

## To know all the secondary storage devices connected or present on our system

    lsblk
    output -> 
    mmcblk0 : main memory card
    mmcblk0p1 : partition 1 (main partition which contains Raspberry Pi OS, /)
    mmcblk0p2 : partition 2 (boot partition, /boot/firmware)

## To know the storage space available in each secondary device and virtual memory allocated to different file systems

    df -h
    output -> 
    Filesystem      Size  Used Avail Use% Mounted on

## To know about OS 

    cat /etc/os-release

## To know the RAM size and other info

    free -h

## To see what network are we connected to

    iw dev wlan0 link

## To see the list of all available networks that we can connect to

    nmcli device wifi list

## To connect to a particular network 

    nmcli dev wifi connect "sameer" password "YOUR_WIFI_PASSWORD"

## To know the python version

    python3 --version

## To know the CPU architecture

    uname -m

## To install system level dependencies

    sudo apt install

## To install inside virtual environment

    pip install

## To download any package or installer

    wget <download_link>

## To install any .sh file

    bash filename.sh

---

# Commands to use for externally conected devices

## To know the peripherals connected via PCIe
    
    lspci

## To check IP address of host connected to our device via SSH

    hostname -I
    output -> IP address of the host device

## To open the configuration file of raspberry pi 5

    sudo raspi-config

## To see all the storage devices connected to our system 
(Linux treats all storage devices as blocks)
(ubuntu mounts all aplications as virtual disks so they will be visible as 'loop')
(then we have internal hard disk drive as 'sda' and solid state drive as 'nvme0n1' along with their partitions if any)
(SD card is mounted as sdb along with its two partitions sdb1(boot) and sdb2 (rootfs) also for this RM value will be 1 indicating that it is removable)

    lsblk

# How to install any application (For example, Zotero)

## Download the file, mostly it will be tar.xz file

## Either extract it using archive using GUI or if using terminal then run the command, 

    tar -xf Zotero-*.tar.xz

## Move it to /opt (it is a system directory specially for third party applications)

    sudo mv Zotero_linux-x86_64 /opt/zotero

## To open /opt folder, go to files, press ctrl + l, then enter /opt

## Now we can run zotero using the command from terminal,

    /opt/zotero/zotero

## Now to make zotero appear in our applications menu, 

    cp /opt/zotero/zotero.desktop ~/.local/share/applications
    nano ~/.local/share/applications/zotero.desktop
    Exec = /opt/zotero/zotero
    Icon = /opt/zotero/icons/icon128.png

Then press windows key and type zotero, we will be able to open zotero application
