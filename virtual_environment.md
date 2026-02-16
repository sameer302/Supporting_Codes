## 1) How to create a python virtual environment ?  
   python -m venv (name of virtual environment) --> windows  
   python3 -m venv (name of virtual environment) --> linux  

## 2) Activating virtual environment in windows cmd.exe  
   deep\Scripts\activate  
   (deep is the name given to venv)

## 3) Activating virtual environment in windows Powershell  
   .\deep\Scripts\Activate.ps1  
   (deep is the name given to venv)

## 4) Activating For Git Bash / WSL / macOS / Linux  
   source deep/bin/activate  
   deep is the name given to venv

## 5) Deactivating virtual environment
   deactivate

## 6) Upgrading pip before installing any package
   pip install --upgrade pip

## 7) Installing any module in our environment
   pip install module_name

## 8) Looking at various packages, modules and libraries installed in our environment
   pip list

## 9) To create a requirements.txt to save all the dependencies of our project
   pip freeze > requirements.txt

## 10) Packages installed via apt are not available to use in a virtual environment unless we create that virtual environment with --system-site-packages flag set during the creation of virtual environment. e.g. of one such package is picamera2
