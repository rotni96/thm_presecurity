# Lab 3 – Audit Local Accounts & Configure Account Lockout Policy

## Objective

Harden the system against brute-force login attacks by setting an account lockout policy. Also, review local accounts to check their status.

Tasks:

- Open `compmgmt.msc`.

- Under Local Users and Groups, review active and inactive accounts.

- Configure an account lockout policy after 3 failed login attempts.

- Take screenshots and verify the policy using: `net accounts`


## Steps Taken

1. Opened `compmgmt.msc` and reviewed **Local Users and Groups**.  
   - Checked which accounts were active or disabled manually.  
   - I realized that doing this one by one can be very slow if there are hundreds of accounts in a company, decided to find solution.
2. I found that I can use PowerShell to export a list of all local users, their status (enabled/disabled), and last login date by using this simple script:
``Get-LocalUser | Select-Object Name, Enabled, LastLogon | Export-Csv -Path "$env:USERPROFILE\Desktop\users_status.csv" -NoTypeInformation``
won't break it down into details now about how it works, because the task didn't mention it, and this is just my addition to the task. This created a clean ``.csv`` file I could open in Excel to quickly review account activity.
3. Opened Local Security Policy (``secpol.msc``) -> Account Lockout Policy and set the following values:
- Account lockout threshold: 3 invalid attempts
- Account lockout duration: 1 minutes
- Reset account lockout counter after: 1 minutes
4. Tried entering the wrong password 3 times on a test user – account got locked. Then I waited to see if it would unlock after 3 minutes, which happened. System worked. This allowed me to view other option to change Account Lockout Policy. I moved to task from the objective afterwards.
5. I set setting policies using the command line:
``net accounts /lockoutthreshold:3``
``net accounts /lockoutduration:15``
``net accounts /lockoutwindow:15``
6. Account got locked after 3 trials. After 15 minutes account got unlocked and I could login.
- After 2 trials I waited 15 minutes to test if I could try again until I locked the account again.

## Evidence

Screenshot from Run Menu:

<img src="../images/run_compmgmt.PNG" width="400" />


Screenshot from Local User and Group Management:

<img src="../images/user_accounts.png" width="600" />

Screeenshot from Test User Properties:

<img src="../images//testuser_properties.png" width="600" />

Screenshot from Excel after sucessful extraction from PowerShell Script:

<img src="../images/user_script_accounts.png" width="600" />

Screenshots from performing `net accounts` command executions:

<img src="../images/lockout_threshold.png" width="600" />

<img src="../images/lockout_duration.png" width="600" />

<img src="../images/lockout_window.png" width="600" />


## Findings

- The account lockout policy successfully blocked login after 3 failed attempts.
- If the lockout window and lockout duration values are not aligned correctly, you’ll get errors when trying to configure them.
- Exporting users using PowerShell is much faster than checking them one by one, especially in larger environments.
- It's faster to perform actions in CLI than in GUI

## Relevance for SOC Analyst

- Lockout policies are essential for defending against brute-force login attacks.
- Misconfiguration (e.g., duration = 0) can cause accounts to remain locked forever unless an admin intervenes.
- SOC teams can monitor account lockouts in event logs to detect suspicious login behavior.
- Exporting user status is useful for auditing and finding unused or disabled accounts that might still pose a risk.
- Brute-force attacks are very common. There are many examples of successful incidents available online, such as the iCloud breach, the T-Mobile attack, or vulnerabilities exploited in Instagram etc.

  Brute-force remains a widely used method and still poses a serious threat to system security. Brute-force attacks can be detected in Event Viewer by monitoring specific event IDs.

