## Random LS stuff
```
ls -al <- shows more!
ls -altr <- recent courses shown first!
ls -larth <- makes it human readable
```
##### U1 vs U2
- On program running, if we run something, even if it has the user as someone else, if you run it, it will show the program urn as the user under someone else
	- You have no choice really.
- (this has some relevance to A1. permissions)
##### Permissions
- Sometimes you make bash scripts where you can't run it.
- There are three parts, you already know it.
	1. Owner
	2. User Group
	3. Others
	```
	groups hacker 
	hacker : hacker g1 <- shows the groups the user is a part of
	grops u2
	u2: u2 <- shows the groups the u2 user is part of
	```
##### Opening the file w/o perms
- The file we saw, hello.txt, using a conveniently placed file, we can ignore the permissions of the file to write using the c script
- There are four commands to change perms:
	1. chmod: Used to change the permissions 
	    - `chmod 666`
	    - `chmod ...`
	1. chown: Used to change the owner
		- `chown u2:u2 example.bash`
	2. chgrp: Used to change group
	3. umask: sets default permissions for newly created files
		- By default, most permissions are `110 110 110`.
		- If we take `111 101 101` and `&` it, you can probably guess what we get.
		- `110 100 100 -> rw--- r-- r--`
		- You can set this mask to set which permissions a file should have
## String formatting
Consider:
```
printf("%x, %x, %x, %x) 
"It just straight up prints the entire stack!"
```
##### Function 3
- In this function, we create area on the heap, then we take the input, then print the input
	- We blindly trust the user's input and just let them input it in.
	- This can be abused to print even more of the stack
	- `%n[numbers]` is used to print numbers characters into the variable that we wish to print
	- This is usually used for verification and compilers
	-
##### Integer overflow
- Integers holds values from -127 to 128
Take 01111111, if ad add 1, we would do:
```
01111111
10000000+
-> twos complement, if we add 1 and the space we haven't isn't enough 
for us to show, it will go into the negatives! So will the opposite.
```
***KEEP THIS IN MIND FOR THE ASSIGNMENT, 3 OR 4 VULNERABILIES CAN BE FOUND WITH INTEGER OVERFLOW***
##### Some random function
```./a.out 65535 123.....
0x0000ffff
0xffff

./a.out 65538 123.....
0x00010002
0x0002
Seg Fault

If the intent wasn't to print just n integers, we can use the integer overflow to change the mem val.
```
#### Root function
- Since the root owns this function, we can run it as (non root?) and run it to maliciously obtain files
- `./fetchfile file2`, this obtains file 2 and prints it!
- `/fetchfile ../..etc/shadow` prints the password of every user of everyone on the VM, encrypted, though.
##### Overtime
