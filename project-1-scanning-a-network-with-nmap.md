# Scanning a Local Network with Nmap

## Introduction

Nmap is a powerful tool for network discovery and security auditing. Network scanning and enumeration are critical skills for ethical hackers, as they help in identifying potential targets and 
vulnerabilities within a network. The goal of this project is to perform basic network scans, identify open ports, and gather information about the devices on your network using a Kali Linux machine.

## Pre-requisites

Kali linux : A Debian based Linux distribution designed for digital forensics and penetration testing.

Nmap : This comes pre-installed on Kali Linux.

A local network with multiple devices connected (computers, printers, IoT devices, etc.).

## Tasks

### 1: Basic Network Scan

Open a terminal on your Kali Linux machine to run a basic scan on your local network with your network's IP range.

`nmap 192.168.110.74/24`

### 2: Scan for Specific Ports

Use the -p option to target a specific port. You should get a list of devices with port 80 open (if they exist).

`nmap -p 80 192.168.110.74/24`

### 3: Detect Versions of Services

Use the -sV option to detect the version of services running on open ports. You should get a detailed list of open ports and the services running on them, including version information.

`nmap -sV 192.168.110.74/24`

### 4: Detect Operating System

Use the -O option to detect the operating systems of devices on the network. You should get back the operating system details of the devices on the network.

`sudo nmap -O 192.168.110.74/24`

### 5: Scan Aggressively

Using the -A option this gives comprehensive information about the devices on the network, including open ports, services, versions and operating systems.

`sudo nmap -A 192.168.110.74/24`
