# Cybersecurity-HomeLab
*Insert software used and description of what we're trying to achieve*

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
    -  