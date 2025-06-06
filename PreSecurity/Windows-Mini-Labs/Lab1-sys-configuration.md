# Lab 1 - System Configuration (msconfig): Boot Configuration Audit

## Objective: 

Check if the system is set to boot in Safe Boot or Diagnostic startup mode. These settings may indicate potential unauthorized changes or malware activity.

Tasks:

- Open msconfig and check if the system is set to boot in Safe Mode or Diagnostic Mode.

- In the Boot tab, confirm that the system is not configured to boot in Safe Mode unless intentionally required.

- Export the list of boot configuration to a screenshot.

## Steps Taken:

1. Opened ``msconfig`` (System Configuration) via Run Menu (``WIN + R`` -> ``msconfig``)

2. In the **General** tab, checked the startup type:
- It was set to Selective startup.

3. In the **Boot** tab, confirmed that:
- The Safe boot option was not checked.
- No additional modifications were found

## Evidence:

Screenshot from Run Menu:

<img src="../images/run_msconfig.png" width="400" />
<br><br>


Screenshots were captured from the following tabs:
- General (showing the startup type)

<img src="../images/general_tab_selective.png" width="500" />

- Boot (showing the Safe Boot option and settings)

<img src="../images/boot_tab_lab.png" width="500" />

## Findings

- The boot configuration was not altered.
- Selective startup is often observed as the default configuration in fresh Windows 10 installations.
- Safe Mode and Diagnostic Mode were not enabled.
- No suspicious configuration found.

## Relevance for SOC Analyst:

- Attackers may change boot settings to hide activity or disable security tools.
- Regularly auditing the `msconfig` settings helps to detect potential security issues.

Although I'm still learning, I already understand that some types of malware modify boot options to force the system into Safe Mode in order to bypass security tools that’s why auditing boot configuration has real analytical value.

In some known attack cases, adversaries have leveraged Safe Mode to disable endpoint protection, since many security tools do not run under minimal boot environments. For example, certain ransomware strains are known to reboot the system into Safe Mode before encryption.

References:
 - https://attack.mitre.org/techniques/T1562/009/ - MITRE ATT&CK T1562.009
 - https://www.picussecurity.com/resource/blog/snatch-ransomware-explained-cisa-alert-aa23-263a - Snatch Ransomware
 - https://www.bleepingcomputer.com/news/security/avoslocker-ransomware-reboots-in-safe-mode-to-bypass-security-tools/ - AvosLocker Ransomware
 - https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-075a - LockBit 3.0
