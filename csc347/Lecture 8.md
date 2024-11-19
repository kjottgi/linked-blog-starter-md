****
Alice and bob** are two people that are trying to communicate
- Eve is just listening to people talking
- Mallory is a malicious attacker but 
**Confidentiality/Privacy**
- We want to make sure E and M can't read
- Only those authorized can read
- We use algorithms to do this.
*Some common examples is https, ssh, which are encrypting.*
**Data Integrity**
- Messages sent between two people should remain in tact and modification should be know
- Anything should not be altered, if so, not change
**Authentication**
- Messages sent between A&B appear in tact (vs M) and A and B should know that a message has been modified
- Written data should not be altered. known if so.
- We want to make sure it's not modified or changed. 
**Authentication**
- Ensure that A knows that she is talking to B and vice versa
- Difficult to define well:
	- Data: Verification of the origin of the data
	- Enrity: Verification of the identity of the entity
- Multifactor Authentication:
	- What you know: user id/password
	- What you have: body data.
**Non-Repudiiation**:
- Ensure that if A says that she will meet B at 8:30 in Tim Hortons, she can't later say that "I did not sa that"
- prevents a entity from denying previous commitments/actions
**Things that fall outside**
- Software registration
**What is more important secrecy or authentication**:
- Authentication is more important in a bank account as you can't do anything with someones balance
**If we are gambling from A to B**
- A interceptor may be able to see the cards and then intercept or change the cards
**Cryptography**
- The system much be practically or mathematically impossible decipherable
	- We use large primes to encrypt
- It must not be required to be secret, it must be able to fall into the hands of the enemy without inconvenience
- Its key must be communicable and retainable without the help of written notes, and changeable and modifiable at the will of correspondents
	- This should be easy and trivial.
- It must be applicable to telegraphic correspondence
- It must be portable and not require multiple people
- The system is easy to use without mental strain nor the knowledge of a long series of rules to observe given the circumstances
**Parts of a cryptosystem**
- Each function is bijective
**Example Caeser/Sub cipher**
- There are 26! permutations, it was secure for a long time
- Certain languages like english have more frequency then others
- You can match up the graphs to align words
- Random vectors acn be used with xor to encrypt, can only be used once.
- Most things are not random, especially the code in the random function
**Clock Cipher(DES)**
- Data encryption stan
- WEP:
	- Shown to be breakable when WIFI until WPA was roken, then WPA2, WPA3, breakable
	- We map each input block to a unique output block
	- the block size makes it impossible for humans to write down 
	- Patterns on the input are showing as patterns on the output
	- Zoom still did this but some companies don't use zoom for this reason assuming it has not been fixed.
	- To fix this, we just use initialization vectors to XOR it to the first block, then use ita s a cipher text to the next block!
	- It's not possible to parralelize this and can be tedious
**AES mode**
- Adds more complexity to the pattern breaking``
0 1199
1 9119
2 
**Secret Colors**:
- Two teams usually pick numbres
```
Alice(yellow)        Bob
g= 7(yellow)         g = 7         
p = 11(3 drops)      p = 11
a = 17[alice chooses 17]
g ^ a % p = 7^17%11 = 6 ->
					b = 23[bob chooses 23]
					g^b % p 
					7 ^ 23 % 11 = 2 
Bob sends over that particular secret, which is 2, and alice sends over

Alice received 2, so 2^17 % 11  = 7
Bob got 6, so bob does 6^23 % 11 = 7
They now both know what they can use as the key for encryption.
```
If the number if very large.
**Man in the middle attack**
- Our adversay can hijack the channel and placing themselves between aliace and bob
- They do their own key exchange getting it from both with both not knowing any better
- How do we ensure that alice is *really* talking to bob?


