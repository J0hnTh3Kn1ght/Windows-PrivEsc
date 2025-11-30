## Windows Hacking (Privilege Escalation Scanner)

PowerEnum/PyEnum is a PowerShell/Python script that helps you quickly spot possible ways to escalate privileges on a Windows machine. It's inspired by tools like PEASS-ng and guides like HackTricks. The goal is to find common misconfigurations, weak permissions, and sensitive data that could be exploited.

Use it only for learning or on systems you’re allowed to test. flaws, and potentially sensitive data across a Windows host.

⚠️ It is intended for educational and authorized penetration testing purposes only.

#### Note: I am a cybersecurity student sharing this project in case it is useful to other students or professionals.

- Scans for misconfigurations that could let someone escalate privileges
- Searches for credentials and secrets buried in files
- Lets you filter by file type
- Uses colors to make results easier to read
- Built to be modular, so you can add your own stuff


## Usage

```powershell
# Run a default scan
.\Scanner

# Look for saved passwords or usernames
.\Scanner -LookForCredentials

# Search specific file types
.\Scanner -LookForCredentials -Extensions ".txt,.xml"

# Just search for certain file extensions
.\Scanner -Searchfiles -Extensions ".docx,.ini"

# Need help?
.\Scanner -h/-help
```

## How It Works

The script checks a few common ways attackers try to escalate privileges:

### Filesystem and Drive Scanning

- Checking Files and Drives
- Looks for files that might have passwords or secrets using keywords.
- Scans for extensions like `.txt`, `.xml`, `.config`
- Tries to spot things like:
  - `password`, `secret`, `token`, `api_key`, `username`
  - Regex-based matching to identify hardcoded credentials and tokens.

### Registry and Service Misconfigurations

- Detects possible misconfigurations that may be exploited by attackers, such as:
  - Weak registry permissions
  - Services with unquoted paths
  - Auto-run registry keys

### Local User and Group Enumeration

- Checks current user privileges
- Looks for users in admin groups they probably shouldn’t be in

### Script Injection and Auto-Elevated Binaries

- Highlights potentially injectable paths
- Looks for binaries or scripts run by higher-privilege users

---------------------------------------------

> ⚠️ **Disclaimer**
>
> This repository contains educational content and tools created solely for authorized and legal use.  
> All scripts and information are intended for **educational and ethical cybersecurity research purposes only**.  
> The author (me) does **not** condone or support any illegal activity and assumes **no responsibility** for the misuse of this content.
>
> It primarily serves as a proof of concept and is intended to raise awareness about cybersecurity.

***Have a good learning/Hacking! :)***
