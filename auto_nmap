import os
import subprocess
import datetime

# Check if the nmap module is installed
try:
    import nmap
except ImportError:
    # If the module is not installed, install it using pip
    subprocess.run(['pip', 'install', 'python-nmap'])
    # Import the module after it has been installed
    import nmap

# Initialize the nmap scanner
nm = nmap.PortScanner()

# Get the hostname of the computer running the script
hostname = os.uname()[1]

# Run nmap with fast os detection on all network connections
nm.scan(arguments='-O --osscan-guess')

# Get the current user and date
user = os.getlogin()
date = datetime.datetime.now().strftime("%Y-%m-%d %H:%M")

# Open a file with the hostname as the filename
with open(hostname + '.txt', 'w') as f:
    # Write the current user and date to the file
    f.write(f'User: {user}\n')
    f.write(f'Date: {date}\n\n')
    
    # Write the results of the scan to the file
    f.write(nm.csv())
