<h1>Windows Persistence Analysis w/ CMD and Powershell</h1>

<h2>Brief Description</h2>
<p>This project involves the analysis of system processes and user accounts using Command Prompt (CMD) and PowerShell. The goal is to perform a thorough examination of the system's processes, user accounts, and related configurations to identify potential security risks and suspicious activities.</p>

<h2>Project Walk-Through</h2>
<br/>
<h3>Export list of running processes</h3>
Command Prompt: <code> tasklist > tasklist.txt </code> > Open Sublime text and filter
<br/>
<img src="https://imgur.com/TnB1AQG.png" height="80%" width="80%" alt="Project Overview Image">

<h3> Determine accounts present on workstation</h3>
Command Prompt: <code> net users</code>
<img src="https://imgur.com/GJm2F50.png" height="80%" width="80%" alt="Project Overview Image">

<h3> Determine accounts in administrators localgroup</h3>
<p> These are accounts with administrative privileges</p>
<p> Command Prompt: <code> net localgroup administrators</code></p>
<img src="https://imgur.com/QU3fChh.png" height="80%" width="80%" alt="Project Overview Image">
<p>Identify Suspicious Administrative Account "ServiceeAccount"</p>

<h3> Identify names of local accounts that can connect to a workstation via RDP</h3>
<p> Using net localgroup "Remote Desktop Users" we can see only 1 account is able to RDP</p>
<p> Command prompt: <code> net localgroup "Remote Desktop Users"</code></p>
<img src="https://imgur.com/ikCSSjN.png" height="80%" width="80%" alt="Project Overview Image">

<h3> Retrieve more information from Suspicious account w/ Powershell</h3>
<p> Powershell: <code> Get-LocalUser -Name (SuspiciousName) | Select *</code></p>
<p> Using this command we can retrieve all properties relating to this account</p>
<img src="https://imgur.com/PFM3cwB.png" height="80%" width="80%" alt="Project Overview Image">

<h3> Identify Running Services on the system</h3>
<p> Powershell: <code> Get-Service | Where Status -eq "Running" | Out-GridView</code></p>
<img src="https://imgur.com/OE9u9av.png" height="80%" width="80%" alt="Project Overview Image">

<h3> Identify Scheduled Services on the system</h3>
<p> Powershell: <code> Get-ScheduledTask | Where State -eq "Ready"</code></p>
<img src="https://imgur.com/xmPNFl7.png" height="80%" width="80%" alt="FTK Imager Memory Capture">

<h3> Investigate Scheduled Task Property</h3>
<p> Powershell: <code> Get-ScheduledTask -TaskName 'ActualtaskName' | Select * </code></p>
<p> Reference triggers property </p>
<img src="https://imgur.com/nWmSgCR.png" height="80%" width="80%">
