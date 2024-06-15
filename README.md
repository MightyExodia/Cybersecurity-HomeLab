# Cybersecurity-HomeLab
- We're installing 2 Virtual machines for the HomeLab
    - Kali Linux (Attacker Machine)
    - Windows 10 

# What is a HomeLab
A HomeLab is a personal, self-contained environment for learning, testing, and experimenting with various technologies

# Tools
VirtualBox: Virtualization software to create and manage virtual machines

# Guide
## Installing the Hypervisor and Windows 10
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
4. Once installed, open VirtualBox and create a new virtual machine. Name it "Windows