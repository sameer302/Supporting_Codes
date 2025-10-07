# 1) How to create a folder in linux terminal
  mkdir folder_name

# 2) How to delete an empty folder
  rmdir folder_name

# 3) How to delete an non-empty folder
  rm -r folder_name

# 4) to know about CPU 
  lscpu

# 5) To update the package list in our system without installing or upgrading anything
  sudo apt update

# 6) To just upgrade the installed packages without installing or removing anything
  sudo apt upgrade

# 7) To install new packages, remove unnecessary packages and also update all dependencies
  sudo apt full-upgrade

# 8) We can also combine 5) and 7) commands together as
  sudo apt update \&\& sudo apt full-upgrade

# 9) To know the peripherals connected via PCIe
  lspci

# 10) To display the system performance
  htop
