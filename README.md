# Cybersecurity-HomeLab
- We're installing 2 Virtual machines for the HomeLab
    - Kali Linux (Attacker Machine)
    - Windows 10 

# What is a HomeLab
A HomeLab is a personal, self-contained environment for learning, testing, and experimenting with various technologies

# Tools
VirtualBox: Virtualization software to create and manage virtual machines
Splunk: A big data platform that collects and manages massive volumes of data and searching for information within it

# Things to note

1. Sandbox Enviorments
    - Just by creating a virtual machine, doesn't mean you're in a sandbox enviornment
2. Create Snapshots
    - This is basically a backup, of a point in time. This can be used to restore the system if anything goes wrong. Always create a Snapshot before you test anyting on your system
    - To create a Snapshot:
        - Go to VirtualBox
        - Select the VM you want to create a snapshot for and click on the "Bullets" menu 
        - Click on Snapshots
        - Click on "Take" to create a new snapshot and set a name for your snapshot
    - To restore a Snapshot:
        - Select the Snapshot you require to rollback to and click on "Restore"
3. Specifications
    - Make sure not to over spec the Virtual Machine if your PC doesn't have the sufficient resources (RAM, CPU etc.)



# Guide
## Installing the Hypervisor and creating the Windows 10 ISO
We are going to be using VirtualBox as our Hypervisor.

1. Go to [VirtualBox](https://www.virtualbox.org/wiki/Downloads) downloads page, and select the download package for your current operating system. 
    > In this tutorial, we will be downloading the package for "Windows hosts"

2. Compare the [checksums](https://www.virtualbox.org/download/hashes/7.0.18/SHA256SUMS) of the file which will verify the integrity of the downloaded packagae to ensure that the file hasn't been tampered with.
    - When you go into the above checksums link, it will provide you with a list of SHA256 hashes
    - Go into the directory where your Windows VirtualBox file has been downloaded to
    - Right-Click anywhere in the folder and select "Open in Terminal"
        > may have to select 'Show more options'
    -  In the Terminal, type in "Get-FileHash Virtual" and hit the **TAB** button. This will autocomplete the file name. Hit **ENTER** and you should be able to see the Hash
    ![Screenshot of terminal window showing the output of the above step](/img/WindowsTerminal.png)
    - Compare the hash you got from the terminal with the hash provided in the VirtualBox website.
    - If they match, you can proceed with the installation
3. Install VirtualBox by following the installation wizard. Accept the default settings
4. There are many places from which you could download a Windows 10 ISO file however, in this guide, we're going to be creating our own Windows 10 ISO file
5. Go to the download page for [Windows 10](https://www.microsoft.com/en-ca/software-download/windows10) and click on the **Download tool now** under the header **Create Windows 10 installation media**
6. Once downloaded, run the tool and **Accept** the notices and license terms
7. On the next window, Select **Create installation media**
![Screenshot of windows 10 installtion media tool giving the option to select to Upgrade PC or Create installation media](/img/Windows10tool.png)
8. You can customise the options given or **tick the box** to use the recommended options. We're going to use the recommended options
![Screenshot of windows 10 installtion media tool giving the option to select to Customise options or use recommended settings](/img/Windows10tool2.png)
9. Select the **ISO file** option on the next window
![Screenshot of windows 10 installtion media tool giving the option to select to USB Flash drive or ISO file](/img/Windows10tool2.png)
10. Follow the next steps and wait until the ISO is created

## Setting up Windows 10 in VirtualBox

1. In the VirtualBox main window, click on **New**
2. Type a name for your Virtual Machine and Select the location of the above windows 10 ISO file
    > If you want to install windows 10 manually, untick the **Skip Unattended Installation** box
    > we're going to tick the box for this guide
3. On the next windows, set the Base Memory to 4GB and 1 CPU processor
    > You can adjust these settings based on your system's capabilities
4. Leave the **Virtual Hard Disk** settings as is
5. Shows the summary of options selected - hit Finish
6. Power on the VM by clicking on the **Start** button
7. Once the VM has loaded up, it will display the Windows 1o setup window
8. Change options as needed or leave as default and hit Next - then Install Now
9. On the **Activate Windows** screen, select 'I don't have a product key'
10. Select Windows 10 Pro and hit Next
11. Accept the license terms and hit Next
12. Select 'Custom: Install Windows only (advanced)'
13. In the 'Where do you want to install Windows' - you can create your own partition or leave as is - hit Next
14. Installation Windows 10 will begin
15. Once installation is complete, you are ready to use your Windows 10 VM in VirtualBox

## Setting up Kali Linux in VirtualBox
> Please note that the default credentials to log into Kali Linux is **"kali/kali"**

1. Go to the [Kali Linux](https://www.kali.org/) and hit Donwload
2. We have 2 options for downloading Kali
    - Installer Images (similar to the ISO file for Windows 10)
    - Pre-built images (Virutal Machine)
    > For this tutorial, we will be downloading the pre-built image and importing into VirtualBox
3. Click on the **Virtual Machines** option
4. Select 64-bit (or 32-bit if your PC doesn't support 64-bit) and click on the **VirutalBox** option
    - You can check whether your pc is 32-bit or 64-bit by doing the following
        - Click on the 'Start' button on your taskbar
        - Search for 'System Information'
        - Under 'System Type' is where you will find whether your pc is 32-bit (x86) or 64-bit (x64)
        ![Screenshot of system information in windows 10 that shows whether your pc is a 32-bit or 64-bit machine](/img/systeminfo.png)
5. Once the download has completed, go ahead and extract the contents of the .7z file to where you prefer
6. Go into the folder where you extracted Kali, and then double click on the ".vbox" file
    > Blue icon
7. In the VirtualBox window, you will see the Kali Linux OS imported

## Properly configuring the Virtual Machine
> This is important for both Windows 10 and Kali Linux VMs
> This is to ensure that whatever it is you're doing on your VM, doesn't spill over the your Host system

1. In the VirtualBox windows, Select your VM (Windows or Kali) and then click on "Settings"
2. Select "Network" on the left side-pane
> If you want to test tools and have access to the internet, you can leave the default setting of **"NAT"**

> If you want to test Malware, you can select **"Internal Netwrok"** which will have the virtual machines in their own network which no access to the Host System or the Internet

> Since we're going to be analysing Malware, we will change the Network
3. In the "Adapter 1" tab, click on the "Attached to:" drop down box and select **"Internal Network"** and set a name for it
> Do this for the other VM's you want part of the same network
4. Now we need to assign a static IP address for both the Windows and Kali Linux machones
    - For Windows:
        - On your taskbar, right-click on the 'globe' icon and select "Open Network & Internet Settings"
        - Scroll down and clock on 'Change adapter options'
        - Right-click on "Ethernet" and select "Properties"
        - Select "Internet Protocol Version 4" abd click on "Properties"
        - Click on "Use the following IP address"
        - Set the IP address to something like **"192.168.20.10"** and hit "Ok"
            - To check the IP address - open up command prompt and type in "ipconfig"
    - For Kali Linux:
        - right-click on the "Ethernet" icon at the top right corner
        - Select "Edit Connections"
        - Select "Wired connection 1" and click on the "gear" icon at the bottom left of the window
        - Select IPv4 Settings
        - Click on "Method" and select "Manual"
        - Click on "Add" and set the IP address to something like **"192.168.20.11"** and Netmask as **"24"**
        - Hit Save
            - to check the IP address - right click anywhere on the screen and select "Open Terminal Here"
            - type in "ip addr show" or "ifconfig" and hit enter
5. Now we check if we have connectivity between our 2 machines (windows & Kali Linux)
    - To ping the Windows machine on Kali Linux:
        - ping 192.168.20.10
        > This wont work because the Windows Firewall is blocking inbound ICMP traffic
    - To ping the Kali Linux machine on Windows:
        - ping 192.168.20.11
        > This works!

## Using Splunk to view Event Logs

1. Download and install Splunk
2. Once installed, open Splunk and click on "Add Data"
3. Under "Local Event Logs", Select "Application, Security & System" and hit Next
4. In "Input Settings", leave everything as default
5. Click on "Review" and then "Submit"
6. Click on "Start Searching"
7. Choose an "Event Code' you want to search for and type it in the "Search" bar
[Screenshot of splunk search for EventCode 4672](/img/SplunkSearch.png)
