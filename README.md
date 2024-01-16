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


<br/>
<br/>
<h3> Identify operating system & Hostname</h3>
Data Artifacts > Operating System Information
<br/>
<br/>
<img src="https://imgur.com/xHuOUMm.png" height="80%" width="80%" alt="Project Overview Image">
<h3> Results:</h3>
<oL> 
<li> Operating System: Windows 8 </li> 
<li> Hostname: WIN-BK3J6TFMHLL </li>
</oL>
<br/>
<h3>Identify file that was downloaded at 2013-12-18 03:02:50 & URL</h3>
Data Artifacts > Web Downloads
<br/>
<br/>
<img src="https://imgur.com/JHKz4Wn.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<h3>Identify the path of "Pier.jpg"</h3>
Data Artifacts > Recent Documents
<br/>
<br/>
<img src="https://imgur.com/1wFAOLU.png" height="80%" width="80%">
<h3> Identify File size of "lib" directory</h3>
Program Files > GIMP 2 > Click on largest partition
<img src="https://imgur.com/gq22YpL.png" height="80%" width="80%">
<h3> Investigate when was Administrator account last accessed </h3>
Navigate > OS Accounts
<br/>
<img src="https://imgur.com/9gCLCyy.png" height="80%" width="80%" alt="Drive Input Selection">

