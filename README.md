# Umbraco CMS 7.12.4 RCE POC / Reverse Shell

## Overview
This repository contains a PoC exploit (https://www.exploit-db.com/exploits/46153) for an authenticated Remote Code Execution (RCE) vulnerability in Umbraco CMS 7.12.4. The exploit leverages a vulnerable XSLT processor to execute arbitrary commands on the server via authenticated access. This script particularly modifies the payload to download and execute the PowerShell script , which spawn a reverse shell (i.e., nishang).

## Requirements
Step 1: Clone the Repository

Atep 2: Install Dependencies
$ pip install requests beautifulsoup4
$ pip3 install requests





## Reference
Original POC: https://www.exploit-db.com/exploits/46153
nishang: https://github.com/samratashok/nishang/blob/master/Shells/Invoke-PowerShellTcp.ps1
