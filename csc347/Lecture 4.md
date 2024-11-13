---
1`:
---
**Plans for today**
- Admin
- Discuss prepared statements
- Terminology and principles
- Break
- Principles and processes
#### Debrief
- On this website, we can give it our email, among other things to submit in the system
- On the PFP, code, we must take some sort of user input.
	- On the case shown, on the particular page, we can send inputs to mess with things.
	- We can even run entire SQL, including deleting the entire database if we wanted to
**Consider some of the cases**
`'and somestuff`
	- This just makes it so we close the previous string in the SQL code
	- This type of injection closes the first string, terminates using ";" and runs some other code 
#### Why don't people fix these errors?
- OWASP Cheat sheet
The fix **"prepare()"**, it just takes the email information literally so something like `' and email=hacker` becomes the literal email value.
- These people just have literal lookups for each language on how to fix the SQL
##### Prepared defenses
- Prepared statements(above)
- Stored procedures
	- Prepared stuff that run int he background 
- Allow list Input-Validation(Whitelisting)
	- Blacklisting is blocking things that you do not want
	- Whitelisting allows certain inputs to only occur vs not allowed
- Escaping user supplies input
	- Sometimes in websites, you need weird % signs
	- Different encoding helps, as if you're encoding the `'`, then it won't break the PHP app, it'll be encoded as something else.
##### Additional Defense
- *Enforcing principles of least privilege*
	- For example, considering the VM, if we want to find all the users that have an account with a password file
	- By having separate accounts, if something like the lesser servers like "FTP", which do not have root
	- This prevents major damage, as those groups cannot do much
- Performing Allow-List Input Validation as a seconday defense
	- Self explanatory 
##### American Cyber security list
##### Terminology
**Vulnerability**: A weakness that can be exploited
- The most common vulnerabilities are things we learned in this course are things like out-of-bounds writes
- Out-of-bounds Read: Using %x on the string
- We have covered most of the top 15 exploits already!
**Exploit:** Using the vulnerability
**Impact**: How this impacts the users and system
1. **Confidentiality:** Information is disclosed to only authorized parties
	1. Things should stay between the intended parties
	2. i.e) Your phone should not be seen by others etc etc (im tired man)
2. **Integrity:** Information remains unchanged in transit and at rest, only authorized parties can change it.
	1. It is fairly easy to label two exploits separately if the impacts are different
	2. Information can change,
	3. i,e) a grade can change along the way
3. **Availability:** Authorized parties have timely and uncompromised access
	1. Do you have timely access to the thing you want to get access to?
There have been some changes since 2020.
- Expanded CIA into Vulnerable CIA and Subsequent System CIA
- You can look this up in the slides man
***-->This is important for tests to know, but for assignments, you don't need to know this really. <--***
#### Compromising?
- Fork Bomb: Availability
- SQL Injections: Confidentiality, Integrity, but also Availability,
- Buffer Overruns: Confidentiality, you can read stuff, Availability can segfault or break data,  Integrity too
- Directory Traversal: Integrity, Confidentiality
##### Authentication and Accountability
**Authentication** : Ensuring** that a user, data or software is genuine
**Accountability**: Maintaining identity of activity logs
### Security and a continuous process
1. Assessment
	1. Analysis of the environment and the system security requirements. During this phase, you create and document a security policy and plans for implementing that policy
2. Protection
	1. Implementation of the security plan
3. Detection
	1. Identification of attacks and policy violations by use of techniques such as monitoring log analysis and intrusion detection
4. Response
	1. Handing of detected intrusions in the ways specified by the security system
#### This course
- **Software Security**: What is bad code, writing good code, buffer overruns, sql injection, xss
- **System Security:** How to protect your system, permissions, scripts, hardware, passwords, intrusion detection, fingerprinting
	- How do you know someone didn't just swap something? 
- **Network Security** : Introducton to networking, firewalls, processes, scanning networks, footprinting, and routing
	- Adding layers of defense
	- Most security has holes, but we can add multiple layers to cover it
- **Cryptography**: How to keep secrets, share them with only specified parties, know you are speaking with whom you intended to speak with
	- 
- Social Engineering: Fishing, people and trust
##### What do we protect?
- Personal security
- Operations security
- Communications security
- Network security
- Information security
##### Other definitions
**Exploit a vulnerability**: Take advantage of a vulnerability
**Prevention**: Preventing something
**Detection**: Knowing that you've been hacked
**Recovery**: After a attack, restoring CIA for example
**Scanning**: Probe ssystems on the internet
**Vulberability Scanner**: A scanning tool that looks for known weaknesses
**Sniffer**: Software that captures network traffic while in transit
**Exploit**: A ready to run programming that takes advantage of known weaknesses
**Social Engineeering**: Exploit human weakness
**Side channel stack**: Eavesdropping, acoustic keyboard eavesdropping
**Root Kit**: Software designed to  hide the fact that a system has been compromised, like replacing ps on a unix system to hide rogue processes
- For example, a virus scanner scans all the files, which are listed via the ls
- If ls gets compromised, the virus scanner is as well!
**Leet**: Slang used by hackers to obfuscate discussions in newsgroups
**Honeypot**: A server that acts as a decoy
- Companies will sometimes put some insecure machines on the internet, to let it go on the internet to let it get infected to see if anything changes
- Cool
**Treat Modelling:** A formal approach to security, 
**Penetration Testing**
**Red Team, Blue Team, Purple Team**
- A defender and a attacker
- It's like TF2
#### andi defense!!
- Virus Total
	- Usually a day behind
- Kali Linux
	- This is an operating system on linux designed by a group of offensive security training 
	- This is for scanning, attacks, stealing, etc, etc..
- Have I been Pwned
- Openwrt.org -> replace router stuff
- Sectools
- Vulnerability Scanners
- Forensics Tools
#### Principles of this course
**Principle #1**: The defender must defend all points, the attacker can choose the weakest point
**Principle #2**: The defender can defend only against known attacks; the attackers can probe for unknown vulnerabilities
**Principle #3**: The defender must be constantly vigilant, the attacker can strike at will
**Principle #4:** The defender must play by the rules; the attacker can play dirty
**Compartmentalize**: Making parts of the system basically
**Perform defense in depth**: Get people to have independent levels of security
**DO NOT volunteer information**: Attackers commonly work in the dark to reconnaissance to get information, don't give it away Bro.
**Fail Safely**: When a system is compomised or a system component fails, it fails such that it changes to a more secure state.
**Simplicity**: Keep things very simply
****
#### Laws of Security
**Law #1**: If a bad actor can persuade you to run his program on your computer, it's not your computer anymore
**Law #2**: If a bad actor can alter the operating system on your computer, it's not your computer anymore
**Law #3**L If a bad actor has unrestricted physical access to your computer...
**Law #4**: If you allow a bad actor to upload programs on your website, it's not your website anymore
**Law #5**: Weak passwords trump strong security
**Law #6:** A computer is only as secure as the administrator is trustworthy
**Law #7:** Encrypted data is only as secure as the decryption key
**Law #8:**....