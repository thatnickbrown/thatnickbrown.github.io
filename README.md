# 🔒 pentesting tools 🔓
*or just 3D-print a captain crunch whistle*
## 💾 PKI on the Fly
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
See the github repo: [PKI on the Fly](https://github.com/thatnickbrown/pkifly)

## 💾 HTTP Header Mirror
Request routers, reverse proxies, load balancers, authentication services, and various other HTTP doodads that sit between clients and backend servers can add or modify headers. HTTP Header Mirror is a web server that prints every header it receives to the page body, simplifying the process of testing for header injection vulnerabilities. HTTP Header Mirror has been helpful in discovering numerous vulnerabilities, including an issue with a CVSS 3.1 Base Score of 10 in a widely used product.

### Usage
```
./mirror.py -a 127.11.22.33 -p 1666
Connect to http://127.11.22.33:1666 to see headers. CTRL-C to quit.
```

### Example page
... using burp to spoof an nginx reverse proxy
![example page](https://raw.githubusercontent.com/thatnickbrown/mirror/main/docs/mirror.png)

See the github repo: [HTTP Header Mirror](https://github.com/thatnickbrown/mirror)

# 🦙 Large Language Model hijinks 🦙
*weak GPUs need not apply*
## 💾 Llama Seance
Summon famous people to chat with using the Llama 2 LLM. Ever wanted to ask Shakespeare to write your cat a sonnet? Or ask Moses which commandments were his least favorite?

### Requirements
- conda/miniconda CUDA environment with [Llama 2](https://github.com/facebookresearch/llama) installed
- either an RTX 4090 or a lot of patience

### Usage
```
 torchrun seance.py --ckpt_dir ../llama/llama-2-7b-chat --tokenizer_path ../llama/tokenizer.model
  ...
The seance will now begin.
Who would you like to summon?
> William Shakespeare

What would you ask William Shakespeare?
> Please write a sonnet about my fat cat Charlie.

Knuckles crack and candles flicker as the summoning begins...
17 seconds later William Shakespeare's ghostly voice is heard:

 Oh, wondrous feline, Charlie, thou art a sight
To behold, with flabby cheeks and round, soft light
  ...
```
See the github repo: [Llama Seance](https://github.com/thatnickbrown/seance)