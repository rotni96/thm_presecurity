# Task 1 Introduction

We will continue our journey exploring the Windows operating system. In this module, we aim to provide an overview of several additional utilities within the Windows OS, including:

- System Configuration
- Computer Management
- System Information
- Resource Monitor
- Command Prompt
- Registry Editor

This module allows us to connect to a VM via a web browser or Remote Desktop.

# Task 2 System Configuration

The System Configuration utility is for advanced troubleshooting, and its main purpose is to help diagnose startup issues. `MSConfig`

## What is System Configuration?

The System Configuration utility finds and isolates issues. When you use this utility, you can select options to temporarily prevent services and programs from loading during the Windows startup process. 

When you use the utility, you can start Windows while common services and startup programs are disabled. Then, you can enable them one at a time. If an issue does not occur when a service is disabled but does when its enabled, the service could be the cause of the issue.

The utility has five tabs across the top. As you can see below:

<img src="images/system_configuration.png" width="600" />

## What do we can find in the tabs?

In the General tab, we can select what devices and services for Windows to load upon boot. The option are: **Normal**, **Diagnostic**, or **Selective**.

In the Boot tab, we can define various boot options for the OS

<img src="images/boot_tab.png" width="500" />


The services tab lists all services configured for the system regardless of their state(running or stopped).

A service is a special type of application that runs in the background. 


<img src="images/services_tab.png" width="500" />


In the Startup tab, Microsoft advises using Task Manager to manage (enable/disable) startup items. The System Configuration utility is **NOT** a startup management program. 

<img src="images/startup_tab.png" width="500" />


In the Tools tab, we can find a list of various utilities, that we can run to configure the operating system further. There is a brief description of each tool. 

<img src="images/tools_tab.png" width="500" />



The main objective of the task was to answer the questions:

**What is the name of the service that lists Systems Internals as the manufacturer?**

Answer: PsShutdown

**Whom is the Windows license registered to?**

Answer: Windows User

**What is the command for Windows Troubleshooting?**

Answer: C:\Windows\System32\control.exe /name Microsoft.Troubleshooting

**What command will open the Control Panel? (The answer is  the name of .exe, not the full path)** 

Answer: control.exe

# Task 3 Change UAC Settings

In this task, we are able to view and modify the settings for the **UAC** (User Account Control), which we discussed in detail in Windows Fundamental 1. These settings can be accessed through the System Configuration panel. 

<img src="images/uac_settings.png" width="600" />

The **UAC** settings can be adjusted or even turned off completely. You can move the slider to preview how the settings will change and see Microsoft's recommendations for each level.

The main objective of the task was to answer the following question:

**What is the command to open User Account Control Settings? (The answer is the name of the .exe file, not the full path)**

Answer: ``UserAccountControlSettings.exe``


# Task 4 Computer Management

The Computer Management tool has three primary sections:

- System Tools
- Storage
- Services and Applications

<img src="images/computer_management.png" width="500" />

## System Tools

Task Scheduler, according to Microsoft, allows us to create and manage common tasks that our computer will perform automatically at specified times.

A task can run an application, a script, send an email or display a message. Tasks can be configured to run at various points, such as at logon/logoff, or on a specific schedule, e.g., every five minutes, an hour, a day, a week etc.

To create a basic task, click on `Create Basic Task` under Actions pane (right side)

## Event Viewer

Event Viewer allows us to view events that have occurred on the computer. These records can be used as an audit trail to understand the activity of the OS. The information is often used to diagnose problems and investigate actions executed on the system.

Event Viewer has three panes.
- The pane on the left provides a hierarchical tree listing of the event log providers.
- The middle pane displays a general overview and summary of events specific to a selected provider.
- The right pane is the Actions pane.

There are five categories of events that may appear in the logs:

<img src="images/five_event_types.png" width="850" />

Image Source: microsoft.com


The standard logs are visible under **Windows Logs**.

<img src="images/standard_log_events.png" width="850" />

Image Source: microsoft.com

## Shared Folders

Shared Folders displays a complete list of shared folders and resources that other users can connect to.

**Shares** - Shows all folders that are shared on the local computer, including administrative shares like: `C$`, `ADMIN$`.

**Sessions** - Displays who is currently connected to the computer via the network and accessing shared resources.

**Open Files** - Lists files that are currently open by remote users

What is it used for?

- Managing access to shared folders
- Monitoring network activity and connected users
- Troubleshooting file access issues over the network
- Manually closing open sessions or files if needed

## Local Users and Groups

The ``lusrmgr.msc`` tool was covered in detail in Windows Fundamentals 1.

## Performance

In Performance we can find utility called Performance Monitor (`perfmon.msc`).

Performance Monitor is used to view performance data either in real-time or in the form of a log file. It's useful for troubleshooting performance issues on a computer system, whether local or remote.

## Device Manager

Device Manager allows us to view and configure the hardware. It serves as the central tool for managing hardware on a Windows system.
It's especially useful when installing new devices or when troubleshooting devices that are not functioning properly.

## Storage

Disk Management is a system utility in Windows that enables you to perform advanced storage tasks. Some of them are:
- Setting up a new drive
- Extending a partition
- Shrinking a partition
- Assigning or changing a drive letter (e.g., A:)

We can also monitor the health of our drives, create virtual disks for testing or virtualization purposes, or even set up RAID software. It's a very useful tool.

What is RAID?

RAID (Redundant Array of Independent Disks) is a data storage technology that combines multiple physical disk drives into one or more logical units to improve performance, redundancy, or both.

## Services and Applications

A service is a special type of application that runs in the background. In this utility, we can do more than enable or disable a service, we can also check its Properties.

Services are essential system processes that handle background operations, such as network communication, security features, or system maintenance tasks. Many services are critical for the system's stability and performance, so we need to be cautious when enabling or disabling them.

We can access Services via Task Manager or by using the command `services.msc`.

## What is WMI?

WMI per Wikipedia: "*WMI allows scripting languages (such as VBScript or Windows PowerShell) to manage Microsoft Windows personal computers and servers, both locally and remotely. Microsoft also provides a command-line interface to WMI called Windows Management Instrumentation Command-line (WMIC)."

WMI enables administrators to manage and monitor computers or servers, both locally and remotely. It provides a way to check the status of systems, including hardware, services, and running processes, making it especially useful for managing multiple machines.

Why is WMI Useful?

- **Administration**: It’s commonly used by system administrators to monitor system health, configure settings remotely, and collect performance data.

- **Automation**: Helps automate repetitive tasks like checking system status or updating settings across multiple machines.

- **Troubleshooting**: Provides detailed information about system issues, which can be helpful when diagnosing problems.

The ``wmic`` command-line tool is deprecated in newer versions of Windows, and Microsoft recommends using PowerShell with CIM or WMI cmdlets instead.

# Task 5 System Information

System Information (`msinfo32`) tool gathers information about your computer and displays a comprehensive view of your hardware, system components, and software environment, which can be used to diagnose computer issues.

<img src="images/system_information.png" width="1150" />

The information in System Summary is divided into three sections:
- Hardware Resources
- Components
- Software Environment

<img src="images/system_information_1.png" width="170" />

**System Summary** displays general technical specifications for the computer, such as OS Name and version, BIOS version, components etc.

The information displayed in **Hardware Resources** is not intended for the average computer user, and I most likely won't need it. Therefore, I don't want to go into detail. (For reference, visit: https://learn.microsoft.com/en-us/windows-hardware/drivers/kernel/hardware-resources)

Under **Components**, we can find specific information about the hardware devices installed on the computer.

In the **Software Environment** section, you can see information about software baked into the operating system and software that you have installed. Other details are visible in the section as well, such as the **Environment Variables** and **Network Connections**

**Environment Variables** store system information, such as the OS path, the number of processors used by the OS, and the locations of temporary folders. They are used by the OS and programs to access system resources (e.g., WINDIR defines the Windows installation directory).

Another method to view environment variables is via ``Control Panel`` > ``System`` > ``Advanced system settings`` > ``Environment Variables``, or through ``Settings`` > ``System`` > ``About`` > ``System info`` > ``Advanced system settings`` > ``Environment Variables``.

Toward the very bottom of this utility, there is a search bar. You can use it to find what we're looking for. 

Objective of this task was to answer questions, which I did!

# Task 6 Resource Monitor

The Resource Monitor (``resmon``) displays CPU, memory, disk, and network usage per process, showing details like file handles and modules. It allows advanced filtering to isolate data for specific processes, manage services (start, stop, pause, resume), and close unresponsive applications. It also helps identify deadlocked processes and file locking conflicts, enabling resolution without closing applications and risking data loss.

As some of other tools mentioned in this room, this utility is geared primarily to advanced users who need to perform advanced troubleshooting on the computer system 

In the Overview tab, Resmon has four sections:

- CPU
- Disk
- Network
- Memory

<img src="images/resource_monitor.png" width="800" />

Note that each tab has additional information for each. 


<img src="images/resource_monitor_tabs.png" width="400" />

CPU Tab: Displays CPU usage per process, services, and the overall system.

Memory Tab: Shows memory usage by processes and services.

Disk Tab: Provides details on disk activity and which processes are using the disk.

Network Tab: Displays network usage per process, including IP addresses and port numbers.


Objective of this task was to answer questions. Done.

# Task 7 Command Prompt

In early operating systems, the command line was the only way to interact with the OS.
When the GUI was introduced, it allowed users to perform complex tasks with a few clicks instead of entering commands in the command prompt.

<img src="images/cmd.png" width="800" />

In this task, we will cover a few commands that a computer user can run in the command prompt.

The command ``hostname`` will output the computer name.

The command ``whoami`` will output the name of the logged-in user.

Let's look at the commands that are useful for troubleshooting.

The command ``ipconfig`` will show the network address settings for the computer.

Each command has a help manual that explains the expected syntax and additional parameters that can be used to the command's functionality.

To retrieve the help manual for a command, use  ``/?`` for example: ``ipconfig /?``.

To clear the command prompt screen use ``cls`` command.

The command ``netstat`` will display protocol statistics and current TCP/IP network connections. 
NOTE: ``netstat`` can be run on its own or with parameters. Each parameter modifies the output. You can combine parameters to see more detailed information.


The command ``net`` is primarily used to manage network resources. This command supports subcommands.
If you type ``net`` without a subcommand, the output will show the syntax for the root command showing a few of the subcommands you can use.

NOTE:  For the ``net``, ``/?`` will not work. In this case, you need to use a different syntax: ``net help``.

To see a comprehensive list of commands, visit: (https://ss64.com/nt/)

# Task 8 Registry Editor

The Windows Registry is a **central hierarchical database** used to store configuration information for the system, users, applications and hardware devices.

Key Functions:

- Stores user profiles.
- Contains informmation about installed applications and the types of documents they can create.
- Stores property settings for folders and application icons.
- Keeps track of hardware connected to the system.
- Monitors ports being used.

The registry is meant for advanced users. Making changes to it can impact the system's performance and functionality.

One way to view and edit the registry is through the Registry Editor (``regedit``).


# Task 9 Conclusion

Recall that the tasks covered in this room were some of the tools that can be launched from ``MSConfig``. Throughout the room, we discovered commands and shortcuts for these utilites. This means we don't need to open ``MSConfig`` every time to run these tools.

Some of the tools listed in ``MSConfig`` that weren't mentioned in this room were left for you to explore on your own!