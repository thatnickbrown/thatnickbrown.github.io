# 🔬 Cybersecurity Research
Curiosity ```kill -9 cat```
## LLM-generated code: unsafe at any clock speed?
It's amazing that large language models can write working software based on minimal descriptions. The security of that code is equally amazing. Check out my research into the subject at the link below.

💾 [LLM security research available on github](https://www.nick-brown.com/llm_security/)

# 🔓 pentesting tools
*or just 3D-print a captain crunch whistle*
## PKI on the Fly
Building your own PKI and issuing server, client, and email certificates is often useful during security testing, but the openssl command line interface is not streamlined for this purpose. I wrote PKI on the Fly to make it easy to create and manage a PKI for penetration testing.
### Usage
```
  Create a root CA named MyCa:
   /pkifly.py ca MyCa
  Create a server cert and key signed by MyCa
   ./pkifly.py server MyCa --servername pentest.target.su
  Create TLS client cert and key signed by MyCa
   ./pkifly.py client MyCa --clientname bobsmith
  Create an S/MIME email cert and key signed by MyCA
   ./pkifly.py email MyCa --email bobsmith@target.su
```
💾 See my github repo: [PKI on the Fly](https://github.com/thatnickbrown/pkifly)

## HTTP Header Mirror
Request routers, reverse proxies, load balancers, authentication services, and various other HTTP doodads that sit between clients and backend servers can add or modify headers. HTTP Header Mirror is a web server that prints every header it receives to the page body, simplifying the process of testing for header injection vulnerabilities. HTTP Header Mirror has been helpful in discovering numerous vulnerabilities, including an issue with a CVSS 3.1 Base Score of 10 in a widely used product.

### Usage
```bash
./mirror.py -a 127.11.22.33 -p 1666
Connect to http://127.11.22.33:1666 to see headers. CTRL-C to quit.
```

### Example page
... using burp to spoof an nginx reverse proxy
![example page](https://raw.githubusercontent.com/thatnickbrown/mirror/main/docs/mirror.png)

💾 See my github repo: [HTTP Header Mirror](https://github.com/thatnickbrown/mirror)

## sarlacc-smtp Email Honeypot
An SMTP honeypot that writes everything it receives to disk.

### Usage
```bash
$ ./sarlacc-smtp.py
creating email server controller
starting email server controller
sarlacc-smtp is listening on port 10025
```
💾 See my github repo: [sarlacc-smtp](https://github.com/thatnickbrown/sarlacc-smtp)

# 🦙 Large Language Model projects
*weak GPUs need not apply*
## TenXLlama
Who needs a 10x programmer when you have a TenXLlama? Just tell the Llama what you want your program to do in plain English and it will spit out fully functional code, ready to run.
### Example
Ask it to write a server, then run it:
```
$ torchrun tenxllama.py
  ...
TenXLlama will write any program you like.
What would you like the program to do?
➡️ listen for UDP packets on port 2222 and print their contents
What would you like to call your program?
➡️ llama_listens
Your program is complete. You can run it with ./llama_listens (assuming you have the required modules.)
$ ./llama_listens
han shot first
bring back firefly
```
Ask it to write a client, then use it...
```
$ torchrun tenxllama.py
  ...
TenXLlama will write any program you like.
What would you like the program to do?
➡️ send its command line argument via UDP to port 2222 on localhost and then exit
What would you like to call your program?
➡️ llama_speaks
Your program is complete. You can run it with ./llama_speaks (assuming you have the required modules.)
$ ./llama_speaks "han shot first"
$ ./llama_speaks "bring back firefly"
```
When studying AI in college this kind of thing would have seemed like sci-fi. It turns out 7 billion neural net parameters ought to be enough for anybody.

💾 See my github repo: [TenXLlama](https://github.com/thatnickbrown/tenxllama)

## Llama Seance
Summon famous people to chat with using the Llama 2 LLM. Ever wanted to ask Shakespeare to write your cat a sonnet? Or discuss shipbuilding with Noah? Now you can.
### Example
```
torchrun seance.py
  ...
The seance will now begin.
Who would you like to summon?
> William Shakespeare

What would you ask William Shakespeare?
> Please write a sonnet about my fat cat Charlie.

Knuckles crack, candles flicker, and curtains gently waft as the summoning begins...
17 seconds later William Shakespeare's ghostly voice is heard:

Oh, wondrous feline, Charlie, thou art a sight
To behold, with flabby cheeks and round, soft light
  ...
```
💾 See my github repo: [Llama Seance](https://github.com/thatnickbrown/seance)
