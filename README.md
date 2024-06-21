<h1>Windows Security Full Scan</h1>
<h2>Description</h2>
This project focuses on performing a comprehensive security scan on a Windows operating system using Windows Security tools. The aim is to ensure the system is free from malware, viruses, and other security threats. This project includes running a full system scan, scheduling regular scans using Command Prompt (CMD) and PowerShell, and understanding different scan types to maintain system integrity and security.
<h2>Key Objectives</h2>
Perform a Full Scan with Windows Security:
Open Windows Security from the search bar.
Navigate to Virus & Threat Protection.
Select Full Scan and start the process.
Differentiate between MRT and Windows Security Full Scan:
Explain the purpose and benefits of MRT (Malicious Software Removal Tool) and how it differs from the comprehensive scan offered by Windows Security.
Run Scans Using CMD and PowerShell:
Execute quick, full, and custom scans using CMD and PowerShell commands.
Understand different scan types and their specific purposes.
Schedule Regular Scans:
Schedule daily quick scans and weekly full scans using CMD.
Learn how to manage and delete scheduled tasks.
Monitor and Manage Scans:
Use Task Manager to monitor and stop scans if necessary.
<h2>Languages and Utilities Used</h2>
Languages: Command Prompt (CMD), PowerShell
Utilities: Windows Security, Task Scheduler
<h2>Environments Used</h2>
Operating Systems: Windows 10, Windows 11
Tools: Windows Security, Task Manager
<h2>Program Walk-through:</h2>
The primary difference between MRT (Malicious Software Removal Tool) and Windows Security Full Scan lies in their scope and purpose:

MRT (Malicious Software Removal Tool): This is a Windows utility developed by Microsoft to remove specific prevalent malware families from infected systems. It targets known malware and is released monthly as part of Windows Update. MRT is designed to complement antivirus software and provide an additional layer of defense against prevalent threats.

Windows Security Full Scan: This is a feature of Windows Security (formerly Windows Defender) that performs a thorough scan of the entire system, checking for malware, viruses, and other potentially unwanted software. Unlike MRT, which targets specific malware families, the Windows Security Full Scan examines all files and system areas for any signs of malicious activity.

Performing Windows Security Full Scan:

Open Windows Security: Search for "Windows Security" in the Windows search bar and select it from the results.
<img src="https://i.imgur.com/AsJr8qe.png">
Navigate to Virus & Threat Protection: Click on "Virus & threat protection" in the Windows Security dashboard.
<img src="https://i.imgur.com/S1DWAVs.png">
Initiate Full Scan: Select "Full scan" and click on "Scan now" to start the scan, which may take between 1 to 5 hours.
<img src="https://i.imgur.com/RBAHfjQ.png">
<img src="https://i.imgur.com/ZEQQsrS.png">
Performing Full Scan and Quick Scan using Command Prompt:
<img src="https://i.imgur.com/klljNYK.png">
Open Command Prompt as Administrator: Search for "cmd" in the Windows search bar, right-click 
on "Command Prompt," and select "Run as administrator."
<img src="https://i.imgur.com/klljNYK.png">
Execute Commands for Scan Types:
For Quick Scan: Enter "C:\Program Files\Windows Defender\MpCmdRun.exe" -Scan -ScanType 1.
<img src="https://i.imgur.com/49MIsEK.png">
For Full Scan: Enter "C:\Program Files\Windows Defender\MpCmdRun.exe" -Scan -ScanType 2.
<img src="https://i.imgur.com/R0IY3Db.png">
Schedule Scans using Command Prompt:
For Quick Scan: Use schtasks /create /SC DAILY /TN "Windows Defender Quick Scan" /TR "\"C:\Program Files\Windows Defender\MpCmdRun.exe\" -Scan -ScanType 1" /ST 12:00.
<img src="https://i.imgur.com/nYfCMXY.png">
For Full Scan: Use schtasks /create /SC WEEKLY /D SUN /TN "Windows Defender Full Scan" /TR "\"C:\Program Files\Windows Defender\MpCmdRun.exe\" -Scan -ScanType 2" /ST 12:00.
<img src="https://i.imgur.com/5ynalWO.png">
Deleting Scheduled Scans using Command Prompt:
For Quick Scan: Use schtasks /delete /TN "Windows Defender Quick Scan" /F.
For Full Scan: Use schtasks /delete /TN "Windows Defender Full Scan" /F.
<img src="https://i.imgur.com/PPE2xdA.png">
Performing Full Scan and Quick Scan using PowerShell:
Open PowerShell as Administrator: Search for "PowerShell" in the Windows search bar, right-click on "Windows PowerShell," and select "Run as administrator."
<img src="https://i.imgur.com/h0pE3r0.png">
Execute Commands for Scan Types:
For Quick Scan: Enter start-MpScan -ScanType QuickScan.
<img src="https://i.imgur.com/hdHXW5J.png"> <img src="https://i.imgur.com/Jzle4zJ.png">
For Full Scan: Enter start-MpScan -ScanType FullScan.
<img src="https://i.imgur.com/qxcoqYA.png">
Schedule Scans using PowerShell:
<img src="https://i.imgur.com/wWeiaZ6.png">
For Quick Scan: Use the following PowerShell commands to schedule the scan
Copy code
$action = New-ScheduledTaskAction -Execute "C:\Program Files\Windows Defender\MpCmdRun.exe" -Argument "-Scan -ScanType 1"
$trigger = New-ScheduledTaskTrigger -Daily -At 12:00
Register-ScheduledTask -Action $action -Trigger $trigger -TaskName "WindowsDefender_QuickScan" -Description "Windows Defender Quick Scan"
<br />
<br />
For Full Scan: Use the following PowerShell commands to schedule the scan:
sql
Copy code
$action = New-ScheduledTaskAction -Execute "C:\Program Files\Windows Defender\MpCmdRun.exe" -Argument "-Scan -ScanType 2"
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 12:00
Register-ScheduledTask -Action $action -Trigger $trigger -TaskName "WindowsDefender_FullScan" -Description "Windows Defender Full Scan"
Deleting Scheduled Scans using PowerShell:
<img src="https://i.imgur.com/SNvsrob.png">
For Quick Scan: Use Unregister-ScheduledTask -TaskName "WindowsDefender_QuickScan" -Confirm:$false.
For Full Scan: Use Unregister-ScheduledTask -TaskName "WindowsDefender_FullScan" -Confirm:$false.
