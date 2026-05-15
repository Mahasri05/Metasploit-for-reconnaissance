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

<img width="512" height="274" alt="image" src="https://github.com/user-attachments/assets/7ad54a40-1679-4baa-b1cf-3fbbd4b8e28e" />

```This command displays the IP address and network information of the attacker machine running Kali Linux.```

## Invoke msfconsole:
## OUTPUT:

<img width="381" height="357" alt="image" src="https://github.com/user-attachments/assets/eaf8c30e-b89c-411b-8c44-4a10a9d31d25" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="563" height="453" alt="image" src="https://github.com/user-attachments/assets/8bc38d42-f7be-4efd-bf78-f3671cf21656" />

## Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:

<img width="376" height="302" alt="image" src="https://github.com/user-attachments/assets/7254dba2-827c-4c26-b63f-9800741bd451" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="461" height="365" alt="image" src="https://github.com/user-attachments/assets/3037b0da-e891-402e-a431-fb379a10d42e" />

Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="799" height="583" alt="image" src="https://github.com/user-attachments/assets/0ad69cd3-9ff0-4347-a054-5a317dfb3c23" />
Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="788" height="910" alt="image" src="https://github.com/user-attachments/assets/040ae5d4-ca49-4719-a5dd-d551e3fe7ae8" />

The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="622" height="128" alt="image" src="https://github.com/user-attachments/assets/0c5c84db-20ae-41c7-9b60-ea39bffa1d3d" />

## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="844" height="142" alt="image" src="https://github.com/user-attachments/assets/0951da82-92e1-4062-826d-083f23fd7c75" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="878" height="784" alt="image" src="https://github.com/user-attachments/assets/a8f43a18-e988-44c2-b76f-52e81d90deab" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="863" height="442" alt="image" src="https://github.com/user-attachments/assets/cf42943e-9883-45d2-8088-9937574b42fb" />

Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="557" height="96" alt="image" src="https://github.com/user-attachments/assets/42f14a5e-6d03-4def-9482-015845f0cab6" />

After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="889" height="667" alt="image" src="https://github.com/user-attachments/assets/6ef32e10-65f2-4cde-95d3-7b5f80a35275" />

set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="875" height="317" alt="image" src="https://github.com/user-attachments/assets/c1ec5649-7721-4d82-9471-b41fb38689eb" />

## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
