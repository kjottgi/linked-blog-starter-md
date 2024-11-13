Q4 1/2
- Both are strlen()
Q8:
Returns 0 if same(we were right.)
- We compile and give it to gcc and decompile it.
- Movfuscator, and fed it every known program and did a fuzzy comparison
- Otherwise, you can demovfuscator it.

**Preventing:**
1. **Summary: cyberciti.biz/tips/linux-security.html**
 2. **Encrypted communicaton**
	- We want to make sure when we speak, both ssh and scp are "secure"
	- FireSheep used to steal cookies back in the day, this lead to BlackSheep to alert a user to tell people of FireSheep
	- There is a lot of malware being made daily (300K-400K) daily
3. **Avoid using FTP. Telnet and Rlog/ rsh services on linux**
4. **Minimize programs**
```
dpkg --list -> shows list of programs and versions

```
	- We can use programs, but we want to keep them updated to prevent exploits
	- But updates come with their own exploits
6. **One network service per system or VM iNstance**
	- All our VMS use one network service
	- Docker had this issue, where people cram the same thing in one network service
	- One VM, Docker, ... per network
	- One system should have one purpose.
7. **Keep Linux Kernel and Software up to date**
8. **Use Linux security extensions**
	- This gives you more information and control over your system
	- Sometimes viruses know they are in a VM by making certain system calls where it should know things like times and system calls should be
		- You then have to limit the system call of programs and applications from doing this
		- Malware would run these calls and then see they are not allowed and suicide :skull:
	- In summary, you can sanitize and limit parts of the system
9. **Linux User Accounts and Strong Password Policy**
	- We can use JTR and HashCat to hack, they can still use the same tools as you and work around it.
10. **Set up password aging for linux users for better security**
	- You want to change your username and passwords with time
```
# chage -M 99999 userName
# chage -1 userName
chage -1 arnold
# /etc/shadow
```
11. **Locking user Accounts After Login Failures**
	- After certain login number of attempts
	- 
```
faillog
#loock Linux account
passws -1 userName
#unlock Linux Account
passwd -u userName
```
12. **H**ow Do I Verify No Accounts Have Empty Passwords:?**
```
awk -F: '($2 == "") {print}' /etc/shadow 
# checks passwords
```
13. **Make sure no account other then root has uuid set to 0**
	- Otherwise, they have root.
```
awk -F: '($3=="0") {print}' /etc/passwd
# checks if root uuid has 0
```
14. **Disable root login**
	- Every single line in the passwd file, in the last entry tells you has the shell that each of these runs
	- The student has the "BASH" shell
	- By going into the passwd file, if we give them "SH" shell permissions, then when they run the shell, they get the regular shell.
	- You might want a root account, but people to not log into this root account
		- You can use "/sbin/nologin" to do this
		- It will keep prompting you for password, the terminal will say "it is wrong" but it will just deny you.
15. **Physical Server Security**
	- USBS can be OS's, so you'd want to disable this 
	- For small mistakes, we could boot as a single user and fix ourselves
	- the BIOs can be given a password to prevent modification of the boot sequence
16. **Disable Unwanted Linux Services**
	```
		service --status -all <- shows services that are there
		**Usually, ssh is not enabled, you want to use**
		service ssh start
		service ssh stop <- to turn it on/off
	Systemmd:
		systemctl 1 
		systemctl status 
		systemctl status ssh <- tells you info about the program
		
		systemctl disable service #disable/enable at startup
		systemctl1 disable httpd.service #disable/enable at startup
		
		journalctl1 -u, -u, network.service, ssh.service <- all of this is info
		
		netstat -tulpn <- shows what's using what on the web!
	
	```
17.  **Find listening network ports**
18. **Delete X Window Systems**
	- Delete Systems you don't use
19. **Configure iptables and TCPWrappers based firewalls on linux**
	- You do this to make a minecraft server, remember?
20. **Linux Kernel /etc/sysct1.conf Hardening**
21. **Separate disk partitions for linux systems**
	- Separate your linux parts so if one fails, you have the others.
	- Andi did this with CSC207 so people don't view other's files :skull:
```
managed in /etc/fstab
/dev/sda5 /ftpdata ext3
```
22. Disk Quotas
	- Can be managed at the volume level for both users and groups
	- So /home can have both users and groups quotas enforced 
23. Turn off IPv6 only if you are NOT using it on Linux
24. Disable unwanted SUID and SGID Binaries
	-  Gtfobins.github.io, we can pick a command and permission and run a command 
	- This was used in an assignment last year.
```
find / - perm +4000 # suid (find programs with higher prevs)

```
25. **World-Writable Files on Linux server**
	- You can write evrything, chekc is below:
26. **No owner files**
27. **Use a centralized authentication service, (Kerberos)**
	- OpenLDAP is becoming the standard way to maintain accounts across systems
	- THis tracks accounts across all systems, and a central place to manage them.
28. **Logging and Auditing**
	- This is important for A3
	- Everything we do is logged(for good reasons), and are usually in /var/logs
	- Looking at andi's logs:
		- "Evidence of nothing is evidence of something happening" <- look into this for a3
	- There's also kernel logs, among other things
	- Other things like "last" show who logged in and who wasand what they were doing with "w"
	- "faillog" shows people failing to log in correctly
	- "conf" can show ocnfiguration limits, this is a file somewhere in the drive(I can't see it xd)
	- Some of the log files have numbres on the right of it, they are older.
	- **Log Rotation**: If we write to a log, after a while, files get large, so we might not want those, so we make new ones, and compress the old one.
29. [I missed one here.]
30. **Monitor Suspicious and Log mEssages with Logwatch**
	- You can automate checks2. System accounting with audid
	- If you log in at weird places at weird times, this is suspicious
31. System accounting with audid
32. **Secure OpenSSH Server**
	1. We can change ports and then the hackers can't use it if they scanned other #
33. **Install and use Instrusion detection server**
	- Tripwire uses this 
34. **Disable USD/firewall/thunderbold devices**
35. **Disable unused services**
36. **Use fail2ban/denyhost as IDS*install as instrusion detection system***
	- **If a host is rpeatedly trying and fialing logins, then update firewall to ban that ip**
37. **Secure Apache/PHP/Nginx server**
38. **Protecting Files, Directories, and Email**
	```
	gpg --symmetric fileName 
	gpg fileName.gpg <- used to encrypt
	```
39. Backups
```
	deja-dup
	rsync
	git  
```
40. 

## Detecting Processes
- "top" tells you which process is using the most resources, cpu, etc...
- We will pay attention to the "cron" job in "var/log/etc/cron"
```
- Cron basically trims parts out of the shadow and home file and takes it out and puts the output in /home/sid.j
-  This can help us look through and see other files as well.
```
- When you type history, but on some machines, doing commands ending with a space don't get logged, and for 
- You can use the above files to snoop on what other uses do(even if you aren't allowed)
- IN a3 in a VM we give you a vm that has been compromised, find who logged in, and what they did when logging in.
- ``history | grep ssh | grep hell | grep 100``
- 
