# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
![Screenshot (250)](https://github.com/user-attachments/assets/d76ce966-4bc3-46f7-a04d-878b5ea6e42a)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
> systemctl start postgresql

> msfdb init

Invoke msfconsole:
## OUTPUT:
![Screenshot 2024-10-20 170941](https://github.com/user-attachments/assets/440a62f7-eb0c-4dee-84d1-40cb82afa699)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![Screenshot 2024-10-20 171221](https://github.com/user-attachments/assets/a317ac2a-bd89-4ced-894a-6986f4ae9f40)

Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
## OUTPUT:
![Screenshot 2024-10-20 172125](https://github.com/user-attachments/assets/cd992424-98b6-4c49-a8dc-5670b7e28c79)

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
![5](https://github.com/user-attachments/assets/510b37f3-684b-4026-82b4-45453f481f97)

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
![6](https://github.com/user-attachments/assets/a0181c59-c096-4faa-80e6-1f331389314d)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT

![7](https://github.com/user-attachments/assets/68ee16ad-d6c0-4ac4-98c5-78213f814c67)


The info command provides information regarding a module or platform,
![8](https://github.com/user-attachments/assets/d99e2691-cfba-4be1-accd-cfcc4056a2cf)

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
> systemctl start postgresql

> msfdb init

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![9](https://github.com/user-attachments/assets/817e5096-8eb6-4cd3-9a50-7f89ee90f679)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql

![10](https://github.com/user-attachments/assets/eb9e3449-81ba-4cc8-b887-38cf737cafa3)

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version


![11](https://github.com/user-attachments/assets/cbafb8e9-92b6-4d99-8f6c-ee556bf90ac8)

Use the set rhosts command to set the parameter and run the module, as follows:
![12](https://github.com/user-attachments/assets/3855f7bf-e596-4158-a8e2-ddc757e1a122)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![13](https://github.com/user-attachments/assets/f61c9740-5ab5-4046-90d7-40cf9c96f39b)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
> set PASS_FILE /usr/share/wordlists/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
> set RHOSTS <metasploitable-ip-address>

Set BLANK_PASSWORDS to true in case there is no password set for the root account.

>set BLANK_PASSWORDS true

![14](https://github.com/user-attachments/assets/38c66082-ef48-4a0c-a8cd-2d9dd0e4e188)


## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
