# Lab 9: Basic Windows Operations

## Part 1: User Setup
1. Verify Admin Profile:
   - Check if the first profile you created is the admin.
   - In your Google Doc, discuss where to find this setting and how you confirmed it's an admin.
     - Open terminal and enter the following commands
       - `cut -d: -f1 /etc/passwd`
         - this gives a list of user groups
           - in this case I found my user 'andrew'
       - enter the command `groups andrew`
         - this command lists all the groups 'andrew' is part of
           - adm cdrom sudo dip plugdev lpadmin lxd sambashare
           - adm: administrators typically used for system log management and access to log files. Can view and analyze log files.
           - sudo: superuser do command group which allows users to execute commands with elevated privileges. Perfomrs admin tasks such as installing software, modifying sysconfigs, and more. Acts as a superuser when necessary.  With great power, etc. etc.

2. Setup a Non-Admin User Profile (Local):
   - Describe the process used to create a non-admin user.
     - `sudo adduser [username]` in my case the new user is named edgelord.
       - you'll be prompted to create a new password and enter the full name, room number, phone number, etc.
       - this user, by default, will have basic user privileges
   - Include a photo indicating one admin user and one non-admin user.
   
3. Test Non-Admin User Access:
   - Log into the computer as the non-admin user.
   - Attempt an admin function (e.g., changing the computer name).
   - Describe the outcome and explain the significance of the admin-user distinction from an organizational security perspective.
     - I couldn't do any admin functions with the non-admin user edgelord.  I also couldn't login from the rdp so I did some admin stuff via the main account and can now rdp into the non-admin account.

## Part 2: System Info
1. View System Information:
   - Open the "Run" menu and run DXDIAG.
     - `inxi -G` to get system info
   - Include a screenshot of DXDIAG.
     - ![DXDIAG](media/lab9%20-%20DXDIAG.png)
   - Describe the graphics processor listed in DXDIAG.
   
2. About Your PC:
   - In the Windows SEARCH bar, search for and open 'About your PC.'
   - Include screenshots of "Device specifications" and "Windows specifications."
   - Rename the computer as desired, reboot, and provide a screenshot of the new 'About your PC' screen indicating the new name.
     - ![Device & Windows](media/lab9%20-%20new%20name.png)

## Part 3: Command Line
1. Command Line Operations:
   - Open the Terminal as Administrator.
   - Include screenshots of the following command line operations:
     - Determine the VM's IP address.
       - ![VM IP](media/lab9%20-%20ipconfig.png)
     - Ping your lab computer from this one.
     - Run a traceroute to google.com.
       - ![Ping](media/lab9%20-%20trace.png)
     - Navigate to the My Documents folder.
     - In My Documents, create a new folder called mydir.
     - List the contents of My Documents in the Terminal.
     - Delete mydir.
       - ![mydir](media/lab9%20-%20mydir.png)

## Part 4: Software Administration
1. Software Management:
   - Locate the Control Panel and navigate to the Add/Remove Programs menu.
   - Include a screenshot.
     - ![Add/Remove Programs](media/lab9%20-%20addremove.png)
   
2. Windows Update:
   - Run Windows Update to check for OS updates and install them.
   - Capture a screenshot of the updater running.
     - ![Updates](media/lab9%20-%20updates.png)
   - Explain why the Version History menu might be useful for administrators.
     - Version History helps the admin know what, when, etc the system was updated and what version is currently running.
   
3. Application Installation:
   - Download and install Google Chrome.
   - Download and install Sumatra.
   
4. Default App and Association:
   - Make Google Chrome your default web browser.
   - Associate Sumatra with PDF (Portable Document Format) files as the default app.
   - Verify this association by opening a PDF file.

5. Final Thoughts:
   - Reflect on the operations performed in this lab assignment.
     - Basic setup tasks that took me longer than anticipated because I couldn't sleep tonight so I got up at like 230am to get my homework done for today.  Lab 9 is a wrap.
   - Prepare your notes for the final.
