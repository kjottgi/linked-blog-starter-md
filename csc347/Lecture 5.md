Today we'll be TRYING to not fall dfdf asleep now
...
##### **If we are analyzing a web server, what do we try to look for?**
- In functions, it is usually main
- For html websites, it's usually *index!*
- We need to identify the _form_, as it usually allows for **user input**
- For the ml file we have:
	- The input just takes input normally without formatting
	- Some others I cba rn lol just watch the recording future me
Looking at the xml some more
- xmp is used in the code
	- **XMP** seems to prevent the code from being read as HTML
	- If we close the XMP tag at the start, and reopen it at the end, we now can break the defense lol
- We have the ability here to send things to the browser
- If we set network traffic and create fake pages on the HTML page we can fake credentials to send people to other places and steal info ( lol )
##### **Cookies**
- Cookies exist on a server and a browser
- Let us use an analogy:
	- Consider a bar, and you being guest1, and another person in the bar being guest2
	- When you go in the pub, you're asked for ID, when you're confirmed, you're given a stamp and allowed in
```
123456: id is ok, beer is 10	
```
- The bar has the id, and if you get another one, they recognize you
	- The server side of things keep tracks of things like a shopping cart, etc etc, dark mode
- Chrome as an attacker had put a bad string in the public parts(like a product review)
- When the safari goes there, loads the bad string, and then the browser sends the cookei to the attackers server and puts it in the attackers cookie then sees what you have in the shopping carts
One input put on one site by one user can be seen by other users.
We can dynamically alter what a browser sends to a user
There are several user input issues
- They should have sanitized the user input inward
- They should have displayed things to the user to not show
##### **Hashing**
- If we look at a hash, it is hard to go backwards to see it
- The first digit of the .
Summary
- Input not being sanitized and being put on other peoples
- Hashing(review) how it's useful and using tools to apply hashing.