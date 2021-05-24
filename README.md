# Vulnhub-MomentumWriteup
Its my First CTF  Write-Up on Vulnhub machines

## Lets Get Started 
### 1) First Get the Target Ip  Address
![Markdown Logo](https://github.com/raj537/Vulnhub-MomentumWriteup/blob/main/screenshots/host-ip-found.png)
### I have used a simple nmap PingSweep scan to detect a the host
```bash
   nmap <target-cidr> -sn
```
### the -sn tells the nmap tool to send ping packets to the host. (Live Host Identification)
-------------------------------------------------------------------------------------------------------
### 2) Perform a Port Scan Against the Target
![Markdown Logo](https://github.com/raj537/Vulnhub-MomentumWriteup/blob/main/screenshots/host-port-scan.png)
###
