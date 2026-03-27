# Active Directory Lab
While studying active directory penetration testing, I was able to set up a virtualized environment to learn more about cybersecurity. While using a linux as host, I used the software called Virtual Machine Manager to host a windows 10 server with two windows 10 client machines. I also created a kali linux machine to be my attacker machine. 

## Tools used
BloodHound
Mimikatz
Impacket
Responder
Metasploit
Nmap
Hashcat
CrackMapExec
ADpeas

## Attack paths
I started by using nmap to scan for devices on the local network I set up for the virtual machines to gain their IPs. Afterwards I scanned ports of the three windows 10 computers using Nmap. SMB port 445 was available on all three of the machines I noticed, but I did not have any credentials to log in. I decided to use Responder to see if I could catch a hash and use hashcat on the NTLM hash. I was able to find a single one for one computer and after a while, I gained the password from the user. With these credentials I was able to log into the computer through Impacket. Since I was able to establish a shell through Impacket, I dumped credentials in order to get as much information as possible, which led me to having the username and password to the other client computer. From here, I got stuck for a while not knowing how to get through to the Domain Controller. I decided to use BloodHound with my credentials I had to map the network and see what my next step can be. Eventually I used a tool named ADpeas, which allowed me to kerberoast and gain access to a privileged service. Finally, I used Metasploit to run an exploit that allowed me to gain access to the system as an administrator.

## What I learned
I took poor notes and I didn't save or take pictures of some of my progress as I was going through the lab. Unfortunately, my kali attacker machine crashed as I got in through to the Domain Controller. Because of this, I didn't have any proof that I was able to root the Domain Controller and I had to go and figure out which of the methods I did worked since I was attempted multiple things. 

I should have done the traditional route of Recon, Scan, Enumerate, Exploit, Escalate, Maintain like how I was taught instead of just testing and trying different things. This wasted enourmous amounts of my time and could have reduced the quality of my pentest report as well as miss vulnerabilities.






