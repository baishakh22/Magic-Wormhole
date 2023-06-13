# Magic Wormhole
This is simple, sercure tool to move files from one computer to another. It is a command line based transfer system. The Magic-Wormhole (Python) distribution provides several things, like an executable tool ("bin/wormhole"), an importable library (```import wormhole```), the URL of a publicly-available Rendezvous Server, those together is their protocol. 

*Rendezvous Protocol is a computer network protocol that enables resources or P2P network peers to find each other. A rendezvous protocol uses a hankshakeing model, unlike an eager protocol which directly copies the data. In a rendezvours protocol the data is send when the destination says it is ready, but in an eager protocol the data us send assuming the destination can store the data. - Wikipedia*

## The Magic-Wormhole Protocol (form their website)
There are several layers to the protocol.

At the bottom level, each client opens a WebSocket to the Rendezvous Server, sending JSON-based commands to the server, and receiving similarly-encoded messages. Some of these commands are addressed to the server itself, while others are instructions to queue a message to other clients, or are indications of messages coming from other clients. All these messages are described in “server-protocol.md”.

These inter-client messages are used to convey the PAKE protocol exchange, then a “VERSION” message (which doubles to verify the session key), then some number of encrypted application-level data messages. “client-protocol.md” describes these wormhole-to-wormhole messages.

Each wormhole-using application is then free to interpret the data messages as it pleases. The file-transfer app sends an “offer” from the wormhole send side, to which the wormhole receive side sends a response, after which the Transit connection is negotiated (if necessary), and finally the data is sent through the Transit connection. “file-transfer-protocol.md” describes this application’s use of the client messages.


## Installation

### MACOS/ OS-X
1. Install the homebrew. ([Homebrew](https://brew.sh/))
2. Run the following command:

```
brew install magic-wormhole
```


### Windows
For windows it's little complicated to install magic-wormhole. We need to install a package manager before install wormhole. So as a package manager, we use ```chocolatey``` which is a universal package manager for windows. This is a open source project. 
To install Chocolatey, follow the proccedures:
1. Open up your powershell with run as administrator.
2. Copy and paste the following command:

```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

3. Wait for a few seccond to install. 
4. Type ```choco``` to see the version and is it installed or not. 

Install magic-wormhole.
Type the following command to install magic-wormhole. You can use CMD or powershell. Both will work. Right after install chocolatey, magic-wormhole might shows some error to install. Restart your pc can solve this. 

```
choco install magic-wormhole
```
*The binaries for Windows are provided from this project: https://github.com/aquacash5/magic-wormhole-exe*


### Linux (Debian/Ubuntu)
Magic-wormhole is available with apt in Debian 9 “stretch”, Ubuntu 17.04 “zesty”, and later versions:

```
sudo apt install magic-wormhole
```


### Linux (Fedora)
Note: magic-wormhole was removed from Fedora starting in Fedora 37. So this command will only work on Fedora 36 and earlier.

```
sudo dnf install magic-wormhole
```


### Linux (openSUSE)

```
sudo zypper install python-magic-wormhole
```


### Linux (Snap package)
Many linux distributions (including Ubuntu) can install “Snap” packages. Magic-wormhole is available through a third-party package (published by the “snapcrafters” group):

```
sudo snap install wormhole
```



## Uses Example

### wormhole send --help
------------------------
using wormhole is easiest way to transfer data between two computer. Every time we send a file, we need to go the directory where the file is located from our terminal. Everytime it generate some few secrect word or code, which we will need for receiving file. Before use the Magic Wormhole we can see the help page to understant better. To checkout the help page, use the following command:

```
wormhole send --help
```

 <img src="photo 1" width="800">

As we can see from the help page, we can send a file and it will generate a secrect code for us to receive the file. We can also send a file with our customize Code by using (--code [code-Message]), beside we can just send a text message, we can even use the ```Tor``` when connecting two computer. 



### wormhole receive -help
------------------------
We can also explore the receive category by using the following command line:

```
wormhole receive --help
```

![Screenshot 2023-05-22 at 12 04 13 AM](https://github.com/baishakh22/Tools/assets/93491482/dd40f917-0f1e-4c95-9a4e-b215a100542e)



### Send a file 
------------------------
To send a file using the following command. My file name was test.txt

```
wormhole send [File Name]
```

![Screenshot 2023-05-24 at 3 05 40 PM](https://github.com/baishakh22/Tools/assets/93491482/74ac0e0c-b52c-4ba1-b77f-c64c606adf11)



### Receive a file
------------------------
To receive this file we need to use the following command, which you need to press "Y" to confirm. Also as we are using terminal to transfer time, we need to make sure where we want to save our file. Before using the receive file, we need to change the directory where we can to save this file. 

```
wormhole receive [Secret Code]
```

![new](https://github.com/baishakh22/Tools/assets/93491482/9538e079-6318-44a4-807a-4fd70103ac29)

Normally the code is generated with a number and two words, and those are connected with dash symbol (-).



### send text message
------------------------
We can also just send a text message, URL to use the --text option. **Must use the Quotation or (-) to connect those words.**

```
wormhole --text ["Text Message"]
```

![Screenshot 2023-05-22 at 12 27 13 AM](https://github.com/baishakh22/Tools/assets/93491482/5eb93140-35e4-46f2-a60f-5250545c9166)

![Screenshot from 2023-05-22 00-27-27](https://github.com/baishakh22/Tools/assets/93491482/b7a705bf-392d-4312-914b-ce593e73b2e5)



### Send with Customize Secrect Code
------------------------
Everytime we send a file, it generate a secret code by the itself. We can also customize this code by using the following command:

```
wormhole send --code [type the code] [File Name]
```

![Screenshot 2023-05-22 at 12 03 15 AM](https://github.com/baishakh22/Tools/assets/93491482/ffd14bfe-8905-4c33-b24c-8e0ff49ed2c7)
![Screenshot from 2023-05-22 00-06-52](https://github.com/baishakh22/Tools/assets/93491482/7c0c5cf8-9c12-4294-a112-9504be9959f4)

Here, my file name was "IMG_7334.JPG". And for the code I used "9-muhfat-alam". Try three different word, and one is number. 


## Using more than one options
------------------------
We can also use more than one option when we send a file. Like I want to send a text messgae and the secret code will be given by me. As an example, I used for text is "Hi This is Muhfat Alam", and my secret code is "3-muhfat-alam"

```
wormhole send --text "Hi This is Muhfat Alam" --code 3-muhfat-alam
```

![Screenshot 2023-05-22 at 12 29 10 AM](https://github.com/baishakh22/Tools/assets/93491482/cb2ee506-09a6-427f-808c-15fe8f7ca7ed)
![Screenshot from 2023-05-22 00-29-39](https://github.com/baishakh22/Tools/assets/93491482/a5930293-e678-4d03-99e5-83bca0619f15)






Note: For more documentation check out this link. Those share more details about security, privacy, protocol, method and behind the code.
1. https://magic-wormhole.readthedocs.io/en/latest/transit.html
2. https://github.com/psanford/wormhole-william











