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

# Commands to use for externally conected devices

## To know the peripherals connected via PCIe
    
    lspci

## To check IP address of host connected to our device via SSH

    hostname -I
    output -> IP address of the host device

## To open the configuration file of raspberry pi 5

    sudo raspi-config


  
