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

##### ii. User Switch
- **Objective**: Switch the session to the newly created user using command-line authentication
- **Commands Used**: 
  ```bash
  su user1

##### iii. Folder and File Creation
- **Objective**: Create a new directory and a file within it. Write a simple message in the file.
- **Commands Used**: 
  ```bash
  mkdir folder1
  echo "Hello from user1!" > folder1/file1

##### iv. Switch Back to Original User
- **Objective**: Switch back to original user session ('ctf').
- **Commands Used**: 
  ```bash
  exit
