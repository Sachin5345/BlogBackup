---
title: "Learning about the Package Manager and Systemctl"
datePublished: Thu Jul 27 2023 06:17:05 GMT+0000 (Coordinated Universal Time)
cuid: clkkriezm000309l4gqvyfbmc
slug: learning-about-the-package-manager-and-systemctl
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690429809075/8ba2738a-d88c-42a2-bdac-caf97c7d4dbd.jpeg
tags: linux-commands, trainwithshubham, tws, systemctlandpackagemanager, understandinglinuxbetter

---

# Voyaging deeper into OS and its tools

While we continue to learn about Linux and its superpowers, there are a few questions that can arise in your mind. I had a few too. I have tried adding those and tried answering them in simple words to the best of my understanding.

The first thing that struck my mind as an infrastructure engineer after learning the commands in Linux was there should be some command which would be enabling me to control the way I can tell the OS or I can command the OS to use and update itself or deploy packages and update them as well. So, I put my explorer cap on and started looking in the manual and internet for answers. I found the answers below as a few solutions.

# Package Manager

A package manager is a software application that allows you to install, update, and manage software packages on a Linux-based operating system. It streamlines the installation process and guarantees that dependencies (additional libraries or packages required for the software to function) are appropriately managed. Package managers differ between Linux distributions, but they all fulfill the same goal.

You could ask me a quick question here. Sachin, what if I don't use Linux directly and I have a different flavor of Linux that I currently use? Is this still available to me?

The answer is pretty simple... Indeed Yes! you can use the package manager on different flavors of Linux:

* **apt** (Advanced Package Tool) - Used in Debian and Ubuntu-based systems.
    
* **yum** - Used in Red Hat, CentOS, and Fedora-based systems (though it has been replaced by `dnf` in newer versions).
    
* **dnf** (Dandified Yum) - Used in modern versions of Fedora and CentOS.
    
* **pacman** - Used in Arch Linux and its derivatives.
    
* **zypper** - Used in openSUSE.
    

Great!! Let's check that out on a Linux machine (since I already had one spun up with AWS 😉). Let's say, I want to make my server install the httpd service. I would instruct the os, to install httpd.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690431693827/5d4e822a-f9e6-48bc-b30e-412b30a2ba9c.png align="center")

But wait! This needs admin rights!! so I would be using sudo along with yum install httpd. So the command would be:

sudo yum install httpd

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690431540999/58ba3aa3-8e4c-4c04-8948-b20f92c191ee.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690432158673/2bd6b791-c66c-4ff7-bfd6-bf2e17e442c2.png align="center")

See that? The command just installed the httpd package from the repository. Now when I spoke to Ryan (remember the IT guy from the series?), he was glad that I found the package manager tool for my utility. However, he had an added surprise for me. He asked if I knew about the systemctl command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690432463038/ea10bfd6-94cb-4ccd-91c4-128b3c63bd46.png align="center")

Walking around, I met Sharon (another colleague from IT who is command-pro) and asked her if she could tell me about the systemctl.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690433004049/1ac6d407-91ac-4daa-ae33-e4d63ff3b316.png align="center")

# systemctl

The major command-line tool for controlling systemd and its components is systemctl. You can use **systemctl** to start, stop, restart, enable, deactivate, and check the status of your system's services.

wait!! systemd?

**systemd** is a Linux system and service manager. It is intended to be a replacement for the classic SysVinit system initialization used in many older Linux versions. systemd's goal is to optimize the boot process, parallelize service startup, and provide improved system management capabilities.

Remembering that I had installed the httpd service on my Linux machine earlier, I was eager to see how this works. So I jumped to my machine and executed the command systemctl start httpd.

Booooom!! The kernel told me that this is not permitted for you and should be done by the admin or the superuser. That pointed me to use sudo before the command. So I ran sudo systemctl start httpd and guess what!!! Limitless happiness! It worked!!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690434812556/0d82402f-ca9b-46fd-9081-97e80b12a4c6.png align="center")

Now that the command has been executed, I was curious to see if the service started. So, I executed another command sudo systemctl status httpd

The status showed me **active.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690434948555/f8a094c7-9a31-49c4-9a56-9c077c473dd0.png align="center")

The next task was to check if we can stop this service. Looking at the previous set of commands, I now executed, sudo systemctl stop httpd and to confirm, sudo systemctl status httpd

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690435255472/cc967a82-7152-4b05-a60a-68fac8c5f36c.png align="center")

Sure enough! The commands worked seamlessly and service stopped too...

# Uses of systemctl and package managers

## systemctl

* **Managing Services:** systemctl is used to manage system services, which are background processes that run continuously to offer specialized functionality. Systemctl can be used to start, stop, restart, enable, deactivate, and check the status of services. For example, administering web servers, database servers, network services, and system daemons.
    
* **Viewing Service Logs:** You may use systemctl to see logs generated by services, which can help you diagnose problems and monitor system behavior. To read and filter service logs, use journalctl (a systemd component) in conjunction with systemctl.
    
* **Managing Timers:** systemctl may manage timer units, which are used to periodically trigger services or scripts. Using timers, you can schedule tasks to execute at specific intervals.
    
* **Booting and Shutting Down:** systemctl is in charge of managing the boot process and shutting down the system. Systemctl can be used to change the system's default boot target, hibernate, suspend, or power off the system.
    

## Package Manager

* **Software Installation:** Package managers make it easier to install software on a Linux system. They handle package dependencies by automatically resolving and installing the libraries and packages required for a piece of software to function properly.
    
* **Updating Software:** Package managers also ensure that the software installed is up to date. They regularly retrieve the most recent package information from internet sources, making it simple to keep your system up to date with the most recent security patches and bug fixes.
    
* **Software Removal:** Package managers make it simple to delete software from your system. When you uninstall a package, the package management removes any dependencies that are no longer needed.
    
* **Repository Management:** Software repositories, which are collections of software packages hosted online, are managed by package managers. They let you add and remove repositories, providing you access to various software sources.
    
* **Rollback and Downgrade:** Some complex package managers allow you to roll back or downgrade software packages to earlier versions, which is beneficial if a subsequent upgrade creates problems.
    

# Conclusion

Both package managers and systemctl are essential for efficiently maintaining and controlling a Linux system, ensuring that software is up to date and services are working as intended.

Hopeful that the blog was clear to tell you why we use package managers and systemctl and how these can be useful.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690438385263/059552a0-bdde-4c3d-bc70-2d1198dfccfe.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690438467072/2c8e6f01-95ee-4410-8cec-67329d1f2930.png align="center")