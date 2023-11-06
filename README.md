# Failed Brute Force RDP Honeypot with Heat Map


<h2>Description</h2>
<b>Use powershell script to create heat map of Brute Force RDP attacks from arround the world.
</b>
<br />
<br />
The script is used in this demo where I setup Azure Sentinel (SIEM) and connect it to a live virtual machine acting as a honey pot.
We will observe live attacks (RDP Brute Force) from all around the world. I will use a custom PowerShell script to
look up the attackers Geolocation information and plot it on an Azure Sentinel Map!
<br />
<br />

<h2>Steps taken to complete project
</h2>


<p align="center">
Create VM in Microsoft Azure
  
  <a href="https://imgur.com/KxgStxS"><img src="https://i.imgur.com/KxgStxS.jpg" title="source: imgur.com" /></a>
</p>

<h2>
</h2>


<p align="center">
Open Azure Firewall Port 3389(RDP) for exposure to internet
  
  <a href="https://imgur.com/4A03ZK4"><img src="https://i.imgur.com/4A03ZK4.jpg" title="source: imgur.com" /></a>
</p>

<h2>
</h2>

<p align="center">
Connect to VM and setup Powershell Script to Connect logs to API
  
  <a href="https://imgur.com/Qi9Ckou"><img src="https://i.imgur.com/Qi9Ckou.png" title="source: imgur.com" /></a>
</p>

<p align="center">
Create Log Workspace to connect SIEM to Windows 10 logs.
  
  <a href="https://imgur.com/4A03ZK4"><img src="https://i.imgur.com/4A03ZK4.jpg" title="source: imgur.com" /></a>
</p>

<p align="center">
Connect logs to Microsoft Sentinel.
  
  <a href="https://imgur.com/pakVli6"><img src="https://i.imgur.com/pakVli6.png" title="source: imgur.com" /></a>
</p>

<p align="center">
Logs needed to be parsed out from "RawData" field into usable fields.
  
  <a href="https://imgur.com/Mpy8uRA"><img src="https://i.imgur.com/Mpy8uRA.jpg" title="source: imgur.com" /></a>
</p>

<p align="center">
Modified query to remove error in initial connect to API that didn't contain location data. (Manually sorted through logs and IP in logs not included in final map, most still came from Panama)
  
  <a href="https://imgur.com/SOvxlQp"><img src="https://i.imgur.com/SOvxlQp.jpg" title="source: imgur.com" /></a>
</p>

<p align="center">
Final result is heat map showing most attacks coming from Panama
  
  <a href="https://imgur.com/BkeaCJP"><img src="https://i.imgur.com/BkeaCJP.jpg" title="source: imgur.com" /></a>
</p>

<h2>Important note</h2>
I implemented my recommendation to limit IP addresses for port 3389 to only trusted IP Addresses and seen the daily number of attack attempts start at 86,000+ daily drop to none.  This config was done using the Azure Firewall. Number of attacks in heat map was limited to 1000 per day for the plan used by API.  Data added to heat maps were from 3 days, in sessions less than 10 minutes for each logging session.

<h2>Languages Used</h2>

- <b>PowerShell:</b> Extract RDP failed logon logs from Windows Event Viewer
- <b>SQL:</b> Create query to parse data from logs to heat map

<h2>Utilities Used</h2>

- <b>ipgeolocation.io:</b> IP Address to Geolocation API


