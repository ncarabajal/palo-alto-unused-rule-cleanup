# palo-alto-unused-rule-cleanup

This repository contains a Python script designed to automate the management of Palo Alto Networks Panorama devices. The script performs the following tasks:

Connects to multiple Panorama devices.
Fetches device groups and security rules.
Analyzes rule usage and creation dates.
Automatically disables and tags unused rules older than 30 days.
Deletes disabled rules tagged with "kill".
Generates a comprehensive CSV report of the security rules.
Commits changes to the Panorama devices.

## Table of Contents
Features

Prerequisites

Installation

Configuration

Usage

Output

## Features
Automated Rule Management: Automatically disables and tags unused security rules that are older than 30 days.

Rule Deletion: Deletes disabled rules that have been tagged with "kill".

Comprehensive Reporting: Generates a CSV report containing detailed information about the security rules.

Multi-Panorama Support: Connects to multiple Panorama devices and processes each one sequentially.

Secure Credential Handling: Prompts the user for credentials at runtime to enhance security.

## Prerequisites
Python 3.6 or higher: Ensure you have Python installed on your system.

Palo Alto Networks Devices: Access to Panorama devices and the necessary permissions to manage them.

Network Connectivity: Ability to SSH into the Panorama devices.

# Required Python Libraries

pan-os-python: Official Palo Alto Networks Python SDK.
netmiko: Multi-vendor library to simplify SSH connections to network devices.
Other Standard Libraries: csv, re, logging, datetime, collections, getpass.

Install Required Libraries
```
pip install pan-os-python netmiko
```
## Installation
Clone the Repository
```
git clone https://github.com/ncarabajal/palo-alto-unused-rule-cleanup.git
```
Navigate to the Directory
```
cd unused-rule-cleanup
```
Install Dependencies
```
pip install -r requirements.txt
```
Alternatively, install the libraries individually as shown in the prerequisites.

## Configuration
Before running the script, you need to configure the Panorama IP addresses:

Edit the PANORAMAS Dictionary

Open the script file in a text editor and locate the PANORAMAS dictionary. Replace the placeholder IP addresses with the actual IP addresses or hostnames of your Panorama devices.
```
PANORAMAS = {
    "pano1": "PANO_IP",
    "pano2": "PANO_IP",
    "pano3": "PANO_IP"
}
```
Replace "PANO_IP" with your Panorama device details.

## Usage
Run the Script
```
python palo-alto-unused-rule-cleanup.py
```
Enter Credentials

When prompted, enter your Panorama username and password.
```
Enter username: your_username
Enter password:
The password input will be hidden for security purposes.
```
# Script Execution

The script will connect to each Panorama device listed in the PANORAMAS dictionary.
It will perform the automated rule management tasks as described in the features.
Progress and debug information will be logged to the console and the audit_log.txt file.

## Output
CSV Report

For each Panorama device, a CSV file named {panorama_name}-final.csv will be generated.
The CSV report includes detailed information about each security rule, such as device group, rule name, tags, source and destination details, action, usage, and creation date.
Audit Log

The audit_log.txt file records actions taken by the script, such as disabling/tagging or deleting rules.

