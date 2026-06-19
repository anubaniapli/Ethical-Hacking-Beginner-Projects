# Cracking Password Hashes with John the Ripper

## Introduction

John the Ripper is a powerful password-cracking tool available on Linux, macOS and Windows. This project will introduce basic password cracking and highlight the importance of strong passwords.

## Pre-requisites

Kali Linux: A Debian-derived Linux distribution designed for digital forensics and penetration testing.

John the Ripper: Included with Kali Linux.

Hash files: Sample files containing password hashes to be cracked.

## Tasks

### 1: Create Hash Files

Open a terminal and use the text editor nano to create and open a file that will hold the list of password hashes. You can generate the hashes using using services such as KeyCDN's online SHA256 Generator. A simple google search will suffice. Pick simple terms such as 'qwerty' and 'password1'. Copy the hashes before exiting by hitting 'CTRL+X' then 'Y' when asked to "Save Modified Buffer". Finally hit the 'enter' key.

`nano passwords.txt`

Create a second file named wordlist.txt containing the terms used in the hash and other potential passwords.

`echo -e "qwerty\password\password1\123456\nqwerty" > wordlist.txt` 

### 2: Basic Password Cracking

Run John the Ripper to crack the password hashes in passwords.txt. You should see the cracked passwords being displayed.

`john passwords.txt`

### 3: Cracking Using a Wordlist

Use John the Ripper with the custom wordlist to crack the password hashes. John the Ripper should use the custom wordlist to crack the passwords and display the results.

`john --wordlist=wordlist.txt passwords.txt`

### 4: Cracking Shadow File Hashes

Obtain a sample shadow file containing password hashes and extract the hashes from the shadow file into a new file then crack the password hashes. Unshadow is a John The Ripper command.

```
unshadow /etc/passwd /etc/shadow > shadow_hashes.txt
john shadow_hashes.txt
```

### 5: Cracking Passwords with Rules

Use a rules-based approach to crack the password hashes. The following uses John's default rules. Next, use the john --show command to display all cracked passwords. You should see a detailed list of all cracked passwords and their corresponding hashes, highlighting common password patterns.

`john --rules passwords.txt`
`john --show passwords.txt`


