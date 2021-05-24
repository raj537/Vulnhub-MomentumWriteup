# Vulnhub-MomentumWriteup
Its my First CTF  Write-Up on Vulnhub machines

## Lets Get Started 
### 1) First Get the Target Ip  Address
![Markdown Logo](https://github.com/raj537/Vulnhub-MomentumWriteup/blob/main/screenshots/host-ip-found.png)
#### I have used a simple nmap PingSweep scan to detect a the host
```bash
   nmap <target-cidr> -sn
```
#### The -sn tells the nmap tool to send ping packets to the host. (Live Host Identification)
-------------------------------------------------------------------------------------------------------
### 2) Perform a Port Scan Against the Target
![Markdown Logo](https://github.com/raj537/Vulnhub-MomentumWriteup/blob/main/screenshots/host-port-scan.png)
#### Only Port 22(ssh) and 80(http) . I have used TCP-SYN(stealth scan) scan to determine the ports
```bash 
   nmap -sS <target-ip>
```
----------------------------------------------------------------------------------
### 3) Visit the WebPage on Port 80
![Markdown Logo](https://github.com/raj537/Vulnhub-MomentumWriteup/blob/main/screenshots/target-port80-opus-details-id.png)
#### When we click one of the image in the webpage we get a url "http://192.168.60.103/opus-details.php?id=" which is vulnerable to DOM XSS as when we pass anything through the id parameter ,it is reflected in the DOM.
--------------------------------------------------------------------------
### 4) Extract the cookie Via DOM XSS
![Markdown Logo](https://github.com/raj537/Vulnhub-MomentumWriteup/blob/main/screenshots/target-cookie-found.png)
#### We can pass <script> tags via the id parameter , so <script>alert(document.cookie)</script> will alert the cookie .
---------------------------------------------------------------------------------------------
### 5) Run a dirb scan on the target
![Markdown Logo](https://github.com/raj537/Vulnhub-MomentumWriteup/blob/main/screenshots/target-dirb-scan.png) 
#### The dirb scan provide nothing useful information except '/js' directory . On visiting the '/js' directory we can open a file called 'main.js'
-------------------------------------------------------------------------------------------------------
### 6) Note down the SecretPassPhrase
![Markdown Logo](https://github.com/raj537/Vulnhub-MomentumWriteup/blob/main/screenshots/taget-port80-js-mainjs-secretpassphrasefound.png)
#### We can see a AES decryption is performed on 'encrypted' using the passphrase --> "SecretPassphraseMomentum". Well what can be encrypted? Its the Cookie!
--------------------------------------------------------------------------------------------------------------------------
### 7) Decrypt the cookie
![Markdown Logo](https://github.com/raj537/Vulnhub-MomentumWriteup/blob/main/screenshots/target-cookie-found.png)
#### On decrypting the cookie with the passphrase "SecretPassphraseMomentum" we get the username, password . Username --> auxerre , Password --> auxerre-alienum##
------------------------------------------------------------------------------------------------------------------
### 8) SSH the target and get the Flag.
![Markdown Logo](https://github.com/raj537/Vulnhub-MomentumWriteup/blob/main/screenshots/target-flag-found.png)
#### cat the user.txt and get the flag..
-----------------------------------------------------------------------------------------------------------------
   
### Hope this WriteUp Helps
### HAPPY hAcKiNg 
