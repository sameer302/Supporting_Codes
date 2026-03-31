## How to create a python virtual environment ?  
   `python -m venv (name of virtual environment) --> windows  
   python3 -m venv (name of virtual environment) --> linux`  
   Here we write -m to indicate the compiler to create a virtual environment associated with current python version

## Activating virtual environment in windows cmd.exe  
   `deep\Scripts\activate`  
   (deep is the name given to venv)

## Activating virtual environment in windows Powershell  
   `.\deep\Scripts\Activate.ps1`  
   (deep is the name given to venv)

## Activating For Git Bash / WSL / macOS / Linux  
   `source deep/bin/activate`  
   deep is the name given to venv

## Deactivating virtual environment
   `deactivate`

## Upgrading pip before installing any package
   `pip install --upgrade pip`

## Installing any module in our environment
   `pip install module_name`

## Looking at various packages, modules and libraries installed in our environment
   `pip list`

## To create a requirements.txt to save all the dependencies of our project
   `pip freeze > requirements.txt`

### Packages installed via apt are not available to use in a virtual environment unless we create that virtual environment with --system-site-packages flag set during the creation of virtual environment. e.g. of one such package is picamera2

### We can also use conda venv just as we use python venv. The difference between them is that python venv can be used to work only in python environment and so only corresponding packages and libraries can be installed there but conda is more generalized and can be used to install other libraries also. We can use pip install command in conda venv also. One big difference between both is that, if we create 10 python virtual environments and install the same package in each venv then the package will occupy 10 times disk space but in conda, the package installed in any venv gets downloaded to a shared base directory and then later in any venv we just store the hyperlink to the files in the base directory. This helps to avoid redundancy of files
 
