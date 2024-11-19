### Some common registers
We recall memory, how C is turned into assembly, and how memory works. but here are some common registers:
- ESP: Stack Pointer
- EBP : Current stack, frame pointer
- EAX, EBX, ECX, EDS, are general purpose registers
- eip: the instruction pointer
- $pc: PROGRAM counter, use display/i $pc to display program counter
# Running Random functions with GDB
- We need to compile with the -g flag to properly obtain information from GDB via a smyobl table
- ***list main: s***hows the code
- ***info registers:*** shows registers
- **b line***: brkas at a line
- **set var c[0] = 12** Setting a variable at c[0] as 12. 
```
x/32 $esp -> examine top of stack, the stakc pointer, and print 32 words
from it

Each block is 4 bytes, 

0x0bffffc80: c80, c84, c88, c8c
```
Via the stack, when we subtract something from the stack, we are moving it downward, so we are growing it into the spare memory:
![[Pasted image 20241115170142.png]]
Everything pushed after EBP is the locals, everything before may be a parameter.
#### To call a random function:
- Find a vector[i.e a stack] that you can manipulate past the point you are supposed to
- Find where EBP is, and the return is 4 more from there[counting 0].
- Find the reference of EBP to the vector you have, and add.
- ![[Pasted image 20241115172055.png]]


# Breaking the Stack

# week 8 - network basics
We have global internet service providers
- In between each region, there are frames inbetween two parts

If you want to send a piece of data
- If you allocate 1 minute to each person, you can service to infinite but it takes a lot of time
- We then switch and put the packets together
- ![[Pasted image 20241116125547.png]]
- using tracerout (website) we can see where the packets go
- ![[Pasted image 20241116125755.png]]
	- What application is used
	- What is the IP?
	- What their device is
	- What their characteristics are
	- What are htey sending
- ![[Pasted image 20241116125914.png]]
- ![[Pasted image 20241116125931.png]]
Packets contain information about parts of the layers of where the packet goes to.


# week 9 - network fundemantals
![[Pasted image 20241118193317.png]]
- The genmask is a overlay ,for example 255,255,255,0 is all one's  we and it with the address.
```
255.255.255.0
and
192.168.10.17
goes to 
192.168.10.0
then we and it with the next mask. since the first did not work
0.0.0.0
and
192.168.10.17
which gives us
0.0.0.0
```
- Once this matches a destination(0.0.0.0) in this case, we know some things
	- if we have a ip that turns into destination 0.0.0.0
	- The ip should be 10.10.10.10
	- we are on the same network
	- and that we should use the eth0 interface
- Using arp, we can see the hardware address of the gateway, and then we can use that to construct the next packet.
![[Pasted image 20241118194101.png]]
![[Pasted image 20241118194223.png]]
In this case, the address becomes 192.168.10.0, with ETH1 to 0.0.0.0
- If we end up on all 0's, we end up one up with a network one up
- We sernd it to eno1
- ![[Pasted image 20241118194602.png]]
- It doesn't make the same packet, it has to deal with the IP address as well being sent up.

```
netstat -an shows all the the connected machines.

```
The machine will eventually forget arp command.

**Stateless Firewall**: They look up
**Stateful Firewall:** Maintains information about the current sessions 

ex)
![[Pasted image 20241118201533.png]]
We apply our masks, then go to the gateway, (0.0.0.0), then tells us it's on the same network
![[Pasted image 20241118201602.png]]
If we want to go to google, and can't find it, we send it to 10.10.10.10/.
Now on 10.10.10.10:
![[Pasted image 20241118201703.png]]
Now, we also have 0 matches, if we can't find it, then we won't reply!
![[Pasted image 20241118201748.png]]
Otherwise, we can keep going up on the chai nand find a destination that have a place to forward the packet.
![[Pasted image 20241118201950.png]]
- f we change the policy to "DROP",  via "iptables -P FORWARD DROP"
	- This will drop anything that tries to go through like a ping
- iptables -A FORWARD -s 10.10.10.16 -d 192.168.10.17 -j ACCEPT
	- This is source 10.10.10.16 and destination 192.168.10.17, this allows it to be accepted.
	- ![[Pasted image 20241118202815.png]]
	-  iptables -A FORWARD -d 10.10.10.16 -s 192.168.10.17 -j ACCEPT, this also allows the message back
- -m state --state ESTASLISHED,RELATED -j ACCEPT
	- any established ip or any traffic that is related is allowed
	- 
# Week 10 - Networks
When your home router is being hammered, you got to call the IP to analyze and block the patterns.
![[Pasted image 20241116122321.png]]
- In this diagram, one rule that we're violating is that all three services are in one machine.
- Traffic logging also goes on the firewall, anything else is no longer going through the firewall which is blocking things.
```
If we conside ips, we use the first parts as bits to respresent it


For example, 255.255.255.0 ->
10.10.0/24 (first 24 are used)
11111111 11111111 11111111 00000000
255        255     255      0


10.10.8.0/22 -> to find the ips in scope.
 
(we are only using the first 22.)
11111111 11111111 11111100 00000000
255.       255.       252.  0.

10.10.8.17 -> maps to 10.10.8.0 
00001010 00001010 00001000

10.10.9.17 -> maps to -> 10.10.8.0
00001010 00001010 00001001

[WE AND THIS WITH OUR MASK ABOVE]

10.10.10.233
                  00001010 -> 10.10.8.0
10.10.11.233      
					00001011 -> 10.10.8.0

10.10.12.233  
				  00001100	 10.10.12.0


10.10.10.100/30
First 30 bits are used for addresses, last two are hosts.

10.10.10.100/1
First 30 bits are used for addresses, last two are hosts.








```
- echo "obase=2 252" | bc converts the number(252)  into binary.