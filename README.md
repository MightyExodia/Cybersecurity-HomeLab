# Cybersecurity-HomeLab
- We're installing 2 Virtual machines for the HomeLab
    - Kali Linux (Attacker Machine)
    - Windows 10 

# What is a HomeLab
A HomeLab is a personal, self-contained environment for learning, testing, and experimenting with various technologies

# Tools
VirtualBox: Virtualization software to create and manage virtual machines

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