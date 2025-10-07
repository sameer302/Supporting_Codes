# 1) How to create a python virtual environment ?  
   python -m venv (name of virtual environment) -- windows  
   python3 -m venv (name of virtual environment) -- linux  

# 2) Activating virtual environment in windows cmd.exe  
   deep\Scripts\activate  
   (deep is the name given to venv)

# 3) Activating virtual environment in windows Powershell  
   .\deep\Scripts\Activate.ps1  
   (deep is the name given to venv)

# 4) Activating For Git Bash / WSL / macOS / Linux  
   source deep/bin/activate  
   deep is the name given to venv

# 5) Deactivating virtual environment
   deactivate

# 6) Looking at various packages, modules and libraries installed in our environment
   pip list

# 7) To create a requirements.txt to save all the dependencies of our project
   pip freeze > requirements.txt
