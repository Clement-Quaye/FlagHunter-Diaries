
# FlagHunter-Diaries: Masterschool Cybersecurity CTF Portfolio

**Dive into my cybersecurity journey with the `FlagHunter-Diaries`. This repository showcases my hands-on experience and achievements from the Level Four Room challenges on TryHackMe by Masterschool. From Linux basics to Nmap scan reporting, witness my exploration and conquests in the captivating world of Capture The Flag challenges. Join me on this adventure and discover the flags I've captured!**

## Introduction

Welcome to my Cybersecurity Capture The Flag (CTF) portfolio, inspired by the Level Four Room challenges on TryHackMe by Masterschool. This repository showcases my hands-on experience, problem-solving skills, and theoretical knowledge gained from tackling a series of real-world and gamified cybersecurity tasks.

In this portfolio, you'll find a diverse range of challenges I've undertaken, from file system exploration to Nmap scan reporting. Each challenge tested my skills and added a valuable piece to my cybersecurity learning journey. Whether you're an employer, a fellow enthusiast, or a curious visitor, I invite you to explore my work and witness my growth in the realm of cybersecurity.

Feel free to delve into each section, and I hope you find it as enlightening as I found the experience of working through these challenges!

## Challenges 🔐

### CTF Challenges Overview:

1. [Linux Basics: User and File Management 🐧](#linux-basics-user-and-file-management)  
2. [File System Flags 📂](#file-system-flags)  
3. [Webpage Flags 🕸️](#webpage-flags)
4. [Hidden Flags Challenge 🕵️](#hidden-flags-challenge)
5. [Hash Cracking 🔓](#hash-cracking)
6. [Nmap Scan Report 🌐](#nmap-scan-report)

## Tools/OS/Methodology
1. **VMWare Workstation 17 Player**
2. **Kali-Linux**
3. ```bash
   ssh [user]@IP_Address

### *flag#1: {h4ck3r5_r_us}*

## Linux Basics-User and File Management

#### Overview
This challenge focuses on demonstrating basic Linux command line operations, simulating tasks commonly performed by cybersecurity professionals in system administration or security assessment.

#### Task Details

##### i. User Creation
- **Objective**: Create a new user in the Linux system and assign a password for subsequent login.
- **Commands Used**: 
  ```bash
  sudo adduser user1
- *Screenshot*:
   
   ![UserCreation](https://github.com/Clement-Quaye/FlagHunter-Diaries/assets/67621550/37b29e41-58e5-4ac3-a758-78da2f2d7778)

##### ii. User Switch
- **Objective**: Switch the session to the newly created user using command-line authentication
- **Commands Used**: 
  ```bash
  su user1
- *Screenshot*:
  
   ![SwitchUser](https://github.com/Clement-Quaye/FlagHunter-Diaries/assets/67621550/04ecbed8-798c-488a-aa3c-d70a6df128d0)

##### iii. Folder and File Creation
- **Objective**: Create a new directory and a file within it. Write a simple message in the file.
- **Commands Used**: 
  ```bash
  mkdir folder1
  echo "Hello from user1!" > folder1/file1
- *Screenshot*:
  
   ![Folder-File_Creation](https://github.com/Clement-Quaye/FlagHunter-Diaries/assets/67621550/ad19b49d-fa57-4173-aee8-1a746e71f380)


##### iv. Switch Back to Original User
- **Objective**: Switch back to original user session ('ctf').
- **Commands Used**: 
  ```bash
  exit
- *Screenshot*:
  
  ![SwitchBack](https://github.com/Clement-Quaye/FlagHunter-Diaries/assets/67621550/c395e1a8-0625-4164-9dba-e05ee9383fd0)


## File System Flags

#### Overview
In this challenge, the objective is to navigate through a complex file system and locate hidden flags. The ability to find these flags showcases proficiency in navigating and manipulating the Linux file systems, a vital skill in the realm of cybersecurity.

#### Flags Structure
All flags in this CTF follow the structure: `{T415_15_a_te5t}`. 

#### Task Details
- **Objective**: Find 4 system flags.
  
### i. Finding Flag#1 `find_flag.txt`

- **Commands Used**: 
  ```bash
  find / -name find_flag.txt 2>/dev/null
  cat path/to/find_flag.txt
- *Comments: I used the standard error data stream (stderr==2) to redirect/discard all error messages [due to priviledge limitations] to the /dev/null special file*
   
- *Screenshot*:

   ![Flag_1](https://github.com/Clement-Quaye/FlagHunter-Diaries/assets/67621550/514f216d-0d7d-4927-a4c0-6be407083b0a)

  - *Flag_1*: {F1nd_Fl4g_Fun}
    
### ii. Finding Flag#2 `find_flag.txt` 

### A - FIRST ATTEMPT (Find /)
- **Initial Commands Used**: 
  ```bash
  find / -name "*.txt" 2>/dev/null -exec grep -H "{*}" {} \;
  #Command Breakdown:
  : <<'END_COMMENT' #using the here document ('<<') as a workaround for multi-line comments
  1. find / -name "*.txt" 2>/dev/null --> this block runs a search for txt files using the * wildcard
  2. -exec --> This option/command lets me execute another command on each file that matches the find conditions (no. 1)
  3. grep --> tool for searching specific patterns within files
  4. -H --> option/switch tells 'grep' to print the name of the file along with the matching line
  5. "{*}" --> this argument represents the search pattern [not to be confused with the next one which is a placeholder]
  6. {} --> a placeholder that 'find' uses to hold the current file being processed. When 'grep' is executed {} will be replaced with the current ".txt" file
  7. \; --> end of the --exec command ('\' is an escape sequence for the semicolon)
  END_COMMENT
  
- *Screenshot*:

  ![Flag_2-first_attempt_1](https://github.com/Clement-Quaye/FlagHunter-Diaries/assets/67621550/0a3d919e-fe27-411d-882a-804cbe70cc87)

  ![Flag_2-first_attempt_2](https://github.com/Clement-Quaye/FlagHunter-Diaries/assets/67621550/98ede3cb-e252-4fe3-8ed5-90a630e0039e)
  
- *Comments: The output of this command, although successful, is not an optimal (time-efficient) solution to finding the File System Flags*

  ### B - SECOND ATTEMPT (Find /home)
- **Initial Commands Used**: 
  ```bash
  find /home -name "*.txt" 2>/dev/null -exec grep -H "{*}" {} \;

*Screenshot*:

   ![Flag_2-4](https://github.com/Clement-Quaye/FlagHunter-Diaries/assets/67621550/2bee3715-899c-48a9-8658-fe977f5d0ca9)

- *Comments: The output of this command gave me all three (3) remaining File System Flags (within the /home directory)*

#### File System FlagsList - ALL FOUR FLAGS
  ##### a. *Flag_1*: {F1nd_Fl4g_Fun} -- *[directory: /var/backups/find_flag.txt]*
  ##### b. *Flag_2*: {St0ry_Fl4g} -- *[directory: /home/ctf/flag/story.txt]*
  ##### c. *Flag_3*: {Y0u_G0T_1t} -- *[directory: /home/ctf/flag/6/m/a/s/t/e/r/s/c/h/o/o/l/f_l_a_g.txt]*
  ##### d. *Flag_4*: {H1d3_1n_pl41n_s1gh7} -- *[directory: /home/ctf/.f.txt] -hidden file*


### Webpage Flags

#### Overview
In this challenge, the objective is to uncover flags concealed within webpages. These flags can be tucked away in various places, such as HTML comments or hidden pages. Successfully locating these flags highlights proficiency in web application security and a deep understanding of data handling on the web.

#### Task Details

#### i. Flag from HTML Pages and Comments (/var/www)
- **Objective**: Search the source code of webpages to find flags hidden within HTML comments.
- **Method Used**: 
  ```bash
  find /var/www/html -name "*.html" 2> /dev/null -exec grep -H {*} {} \;

- *Screenshot*:
  
  ![Preliminary_attempt](https://github.com/Clement-Quaye/FlagHunter-Diaries/assets/67621550/b0f5c103-5476-4ce2-b99c-8361dce53f74)

- *Comments: Although the output of this command is also not an optimal (time-efficient) solution to finding the Webpage Flags; it does serve as a good cue on which directory and HTML pages to Inspect*

#### Flags in Index (nano /var/www/html/index.html)

![Index html-Flag1](https://github.com/Clement-Quaye/FlagHunter-Diaries/assets/67621550/ec16d417-6fb4-4b1f-bd72-34ba7392ceb8)

##### a. *Flag_1*: {Another_Web_Flag} 

![Index html-Flag2](https://github.com/Clement-Quaye/FlagHunter-Diaries/assets/67621550/52dab1a8-8125-416b-ab89-0270365b6c2e)

##### b. *Flag_2*: {STUDENT_CTF_Web} 



