# Task 1 Introduction

In this module we will attempt to provide an overview of the security features within the Windows operating system.

# Task 2 Windows Updates

Windows Update is a service provided by Microsoft to push security updates, feature enhancements and patches for the Windows operating system and other Microsoft products, such as Microsoft Defender.

<img src="images/windows_update.png" width="1000" />

Updates are typically released on the 2nd Tuesday of each month. This day is called **Patch Tuesday**.
That doesn't necessarily mean that a critical update/patch has to wait for the next Patch Tuesday to be released. Urgent updates will be pushed by Microsoft via the Windows Update service to the Windows devices.

To see the Microsoft Security Update Guide check here (https://msrc.microsoft.com/update-guide)

*The Microsoft Security Response Center (MSRC) investigates all reports of security vulnerabilities affecting Microsoft products and services, and provides the information here as part of the ongoing effort to help you manage security risks and help keep your systems protected.*

Windows Update is located in Settings. Another way to access Windows Update is from the Run dialog box, or CMD, by running the command `control /name Microsoft.WindowsUpdate`

Throughout the Years, Windows Users have grown accustomed to pushing Windows Update off to a later date or not installing the updates at all. One of the reasons was that Users had to reboot system after a Windows update.

Microsoft notably addressed this issue with Windows 10. The updates can no longer be ignored or pushed to the side until forgotten. Windows updates can only be postponed, but eventually the update will happen and compuiter will reboot. Microsoft provides these updates to keep the device safe and secure. 

# Task 3 Windows Security

*"Windows Security is your home to Manage the tools that protect your device and your data"* - Microsoft.

Windows security can be found in **Settings**.

<img src="images/windows_security_0.png" width="600" />

In the above image, we can find **Protection areas**:

- Virus & threat protection
- Firewall & network protection
- App & browser control
- Device security
- And more
code
Each following task will briefly touch on these areas. Before proceeding, let's provide a quick commend on the status icons:

- **Green** means your device is sufficiently protected, and there aren't any recommended actions.
- **Yellow** means there is a safety recommendation for you to review.
- **Red** is a warning that something needs your immediate attention.

Click on `Open Windows Security`
 
<img src="images/windows_security.png" width="800" />

Next, we'll look at **Virus & threat protection**.

# Task 4 Virus & threat protection

Virus & threat protection is divided into two parts:

- Current threats
- Virus & threat protection settings

## Current threats

Scan options:
- Quick scan - Checks folders in your system where threats are commonly found
- Full scan - Checks all files and running programs on your hard disk. This scan could take longer than one hour.
- Custom scan - Choose which files and locations you want to check.

Threat history:
- Last scan - Windows Defender Antivirus automatically scans your device for viruses and other threats to help keep it safe.
- Quarantined threats - Quarantined threats have been isolated and prevented from running on your device. They will be perodically removed.
- Allowed threats - Allowed threats are items identified as threats, which you allowed to run on your device. 

## Virus & threat protection settings

Manage settings:

- Real-time protection - Locates and stops malware from installing or running on your device.
- Cloud-delivered protection - Provides increased and faster protection with access to the latest protection data in the cloud.
- Automatic sample submission - Send sample files to Microsoft to help protect you and others from potential threats. 
- Controlled folder access - Protect files, folders, and memory areas on your device from unauthorized changes by unfriendly applications.
- Exclusions - Windows Defender Antivirus won't scan items that you've excluded.
- Windows Defender Antivirus will send notifications with critical information about the health and security of your device. 

Virus & threat protection updates:
- Check for updates - Manually check for updates to update Windows Defender Antivirus definitions.  

Ransomware protection:
- Controlled folder access - Ransomware protection requires this feature to be enabled, which in turn requires Real-time protection to be enabled.


# Task 5 Firwall & network protection

What is a firewall?

A firewall is a network security device that acts as a barrier, monitoring and controlling incoming and outgoing network traffic based on predefined security rules. It essentially separates a trusted internal network from untrusted external networks, like the internet. Firewalls can be hardware, software, or a combination of both. 

<img src="images/firewall.png" width="500" />


What is difference between 3 profiles? (Domain, Private and Public)

Domain - The domain profile applies to networks where the host system can authenticate to a domain controller

Private - The private profile is a user-assigned profile and is used to designate private or home networks

Public - The default profile is the public profile, used to designate public networks such as Wi-Fi hotspots at coffee shops, airports, and other locations.

If you click on any firewall profile, another screen will appear with two options: **turn the firewall on/off** and **block all incoming connections**. If you using other provider then Microsoft Defender Firewall you won't be able to disable it.

## Allow an app through firewall

You can view what current settings for any firewall profile are. Several apps have access in the Private and/or Public firewall profile. Some of the apps will provide additional information if it's available via the `Details` button.

## Advanced settings

Configuring the Windows Defender Firewall is for advanced Windows users. 

For best practices refer here (https://learn.microsoft.com/en-us/windows/security/operating-system-security/network-security/windows-firewall/configure)

Command to open the Windows Defender Firewall is `WF.msc`

# Task 6 App & browser control

In this section, you can change the settings for the **Microsoft Defender SmartScreen**.

**Microsoft Defender SmartScreen** is a feature designed to protect users from phishing, malware, and social engineering attacks by checking websites, downloads, and applications for potential threats. 

## Check apps and files

**Windows Defender SmartScreen** helps protect your device by checking for unrecognized apps and files from the web. 

## Exploit protection

Exploit protection is built into Windows10 to help protect your device against attacks. 


# Task 7 Device Security

Even thought you'll probably never change any of these settings, it will be covered briefly.

## Core isolation

**Memory Intergrity** - Prevents attacks from inserting malicious code into high-security processes

**Security processor** - Your security processor, called the trusted platform module (TPM), is providing additional encryption for your device.

## What is TPM?

Trusted Platform Module, is a specialized chip designed to provide hardware-based security functions. A TPM chip is a secure crypto-processor that is designed to carry out cryptographic operations. The chip includes multiple physical security mechanisms to make it tamper-resistant, and malicious software is unable to tamper with the security functions of the TPM.


# Task 8 BitLocker

What is BitLocker?

BitLocker is a Windows security feature that encrypts drives to protect data from unauthorized access. It ensures that if a drive is lost, stolen, or accessed without the proper credentials, the data remains unreadable. 

On devices with TMP installed, BitLocker offers the best protection.

*"BitLocker provides the most protection when used with a Trusted Platform Module (TPM) version 1.2 or later. The TPM is a hardware component installed in many newer computers by the computer manufacturers. It works with BitLocker to help protect user data and to ensure that a computer has not been tampered with while the system was offline."* - Microsoft

To learn more about BitLocker, refer to the official Microsoft documentation (https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/bitlocker/)

# Task 9 Volume Shadow Copy Service

The Volume Shadow Copy Service (VSS) is a Microsoft Windows service that allows you to create snapshots or shadow copies of volumes, even while they are in use. These shadow copies can be used for backups, system restore, or other applications.

The Volume Shadow Copies are stored on the System Volume Information folder on each drive that has protection enabled. 

If VSS is enabled (System protection turned on), you can perform the following tasks from within **advanced system settings**.
- Create a restore point
- Perform system restore
- Configure restore settings
- Delete restore points

From a security perspective, malware writers know of this Windows feature and write code in their malware to look for these files and delete them. Doing so makes it impossible to recover from a ransomware attack unless you have an offline/off-site backup.

# Task 10 Conclusion

In this room, we covered several built-in Windows security tools that ship with the Windows OS to help keep the device protected. There is still so much to explain and cover regarding the Windows OS. To learn more about the Windows OS, you'll need to continue the journey on your own.


