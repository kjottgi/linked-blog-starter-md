### Review
- We said it was bad to communicate in plaintext but every time we wanted to figure what to do  we found loopholes and weaknesses 
- Patterns in the input create patterns in the output
- This depends on the input key, we used the Diffie Hellman Key Exchange
- There is then a loophole so far 
#### Private Key Crytography
- We exchange, but someone can be the man inthe middle and take over 
- We can counteact this by sending a encrypted version of the message to bob 
#### Good hash functions
- Preimage resistance: Different plaintexts should give different images
- Second Preimage resistance: Given a hash, you should not be able to find another input that gives a similar hash
	- A bad hash function, like going mod 10
	- If we take two numbers like 555%10,
	- Another hash like 5 also gives a similar output
- Collision resistance: Given a hash you should not be able to find two that gives the same ash, or it is at least difficult to do so
**Downloading Kali:**
- How are we sure that a website(mirror) is not putting things into our image, how can we trust them?
- Kali is punishing a checksum[]
- If the checksum is exactly the same then it is very unlikely that it has been modified.
- We use a has function
- This has the issue of the key being secret, but how do they exchange the key?
![[Pasted image 20241025152530.png]]
How do we properly establish that bob is sure that he is talking to alice?
- Even though we send a encrypted version from Alice to Bob, the encrypted version is being sent, and then it can be repeated to Bob
- We can have two two encryption once in a while from Bob to Alice to check if she's still the same person, but this does not happen the entire time
**One Shot**: We set up the authentication at the start
**Challenge/Response:** We occasionally send messages to the other person then expect a message back, and the only one who should be able to is the other party.
**Private Key Crypography**: Means the encryption/decryption methods are public but the keys are private
**Public Key Crypography**:
- If we have a message we want to encrypt it 
	- D(d,E(e,m)) = E(e,D(d,m))=m [ order of the encrypt/decrypt does not matter.]
- We make the key public to encrypt, but decrypting is reserved to us
- We can use a hash then encrypt it to send it over to make it even harder

We start with WEP, but if you were there you could get it in seconds, same with WPA 
You can reverse engineer the keys.
WEP(s) -> WPA(m) -> WPA(2) -> WPA(3)
### How can we be sure that that it's bob or mallory using the data?
- idk
- ceritificates just google it shii
#### Internet History n crap
- In the 80s, compared to 15 nodes inthe 1970s, they made more nodes
- smtp was set up for email
- tcp/ip was sent to get all messages
- dns was set up so no more ip just use readable names[name to ip]
- In the 80s they would have hundreds of thousands of nodes
- 