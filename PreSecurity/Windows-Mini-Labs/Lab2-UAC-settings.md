# Lab 2 - Lowering User Account Control & Detecting It

## Objective: 

Simulate and detect suspicious activity related to changes in User Account Control settings.

Tasks:

- Temporarily lower User Account Control (UAC) to the lowest setting.

- Launch an elevated process, such as cmd as Administrator.

- Open Event Viewer, and search for UAC-related events in the System or Security log.

- Export the event log to a .evtx file. 

## Steps Taken:

1. Enabled Event ID 4688 in Local Security Policy to view processes that were created or opened.
2. Enabled Process Command Line in Local Group Policy Editor to view what a potential attacker ran in the command line interface (CLI). 
3. Enabled Event ID 4657 in Local Security Policy to track registry changes.
4. Lowered UAC settings to the lowest level, which disables UAC prompts.
5. Launched Command Line Interface as Administrator and simulated opening a file with malware. (I used the `net` command, but the key purpose was to demonstrate what would be logged.)
6. Opened Event Viewer and found logs:
- Event ID 4688: Indicates that UAC settings were changed.
- Event ID 4657: Shows that `ConsentPromptBehaviorAdmin` was changed from level 5 (default) to level 0.
- Event ID 4688: Shows elevated CMD launch process.
- Event ID 4688: Simulated malware execution.
7. Exported the logs as `.evtx` files to the Desktop.


## Evidence:

Screenshots from the Event Viewer:
- Event ID 4688: UAC Settings

<img src="../images/UAC_settings_4688.png" width="1000" />

- Event ID 4657: `ConsentPromptBehaviorAdmin` value change.

<img src="../images/UAC_registry_4657.png" width="1000" />

- Event ID 4688: CMD process was created.

<img src="../images/cmd_administrator_4688.png" width="1000" />

- Event ID 4688: Malware was injected.

<img src="../images/cmd_malware_4688.png" width="1000" />


## Findings

- UAC settings were altered from default (level 5) to disabled (level 0).
- An elevated command prompt was used to simulate malicious activity.
- The system successfully logged critical events (4688, 4657) that could aid in detection by a SOC analyst.

## Relevance for SOC Analyst:

- Changes to UAC settings: Lowering UAC settings might be an attempt to bypass system defenses, making it easier for attackers to gain higher privileges unnoticed.

- Event ID 4688: This event helps SOC analysts detect when new processes are created, which can show suspicious activity, like command-line execution of malicious programs.

- Event ID 4657: This event helps analysts spot registry changes that could be signs of security issues or methods attackers use to stay on the system.

- Monitoring these events: By watching for these types of logs, SOC teams can spot early signs of privilege escalation or other suspicious behavior before it leads to a full compromise.

