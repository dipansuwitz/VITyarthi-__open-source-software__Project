 Open Source Software Audit Project
 ## Overview

This project presents a practical audit of an open-source application using shell scripting. The objective is to analyze system-level behavior, package management, file permissions, and logging mechanisms while connecting them with open-source principles.

The selected software for this audit is Mozilla Firefox, a widely used open-source web browser.

## Author Information
Name: Dipansu Bhakat
Registration No.: 24BAI10759
Course: Open Source Software (NGMC)
Submission Date: March 31, 2026
## Target Application

Mozilla Firefox
An open-source browser maintained by Mozilla, distributed under the Mozilla Public License 2.0 (MPL 2.0).

## Project Structure
.
├── script1.sh   # System information & environment details
├── script2.sh   # Firefox package inspection
├── script3.sh   # File system audit (permissions & disk usage)
├── script4.sh   # Log analysis utility
└── script5.sh   # Open source manifesto generator
## Getting Started
1. Grant Execution Permission

Before running the scripts, make them executable:

chmod +x script1.sh script2.sh script3.sh script4.sh script5.sh
2. Execute Scripts
🔹 System Report
./script1.sh

Provides details such as OS, kernel version, uptime, and user environment.
Compatible with both Linux and macOS systems.

🔹 Package Inspector
./script2.sh

Checks Firefox installation using:

dpkg (Debian-based systems)
rpm (RedHat-based systems)
Falls back to command lookup if package managers are unavailable.
🔹 Disk & Permission Audit
./script3.sh

Analyzes directory ownership, permissions, and disk usage.

🔹 Log Analyzer
./script4.sh

By default, the script scans common system logs:

/var/log/syslog
/var/log/messages
/var/log/system.log

Custom usage examples:

./script4.sh /var/log/syslog error
./script4.sh /var/log/system.log warning
🔹 Manifesto Generator
./script5.sh

Generates a personalized statement reflecting open-source philosophy and ethics.
## Implementation Highlights
Script 1: Extracts system-level metadata and demonstrates open-source licensing awareness (GPL context).
Script 2: Verifies Firefox installation, retrieves version details, and explains MPL 2.0 licensing.
Script 3: Evaluates filesystem integrity through permission and ownership checks.
Script 4: Performs keyword-based log scanning for system monitoring insights.
Script 5: Connects technical implementation with open-source ideology through automated manifesto generation.

## Notes
Firefox is licensed under MPL 2.0, not GPL.
GPL reference in Script 1 is used only for general system-level open-source context.
Firefox logging is primarily user-based; hence, system logs are used for demonstration.

## Sample Output
Example: System Report
Hostname: ubuntu
Kernel Version: 5.15.0
Example: Directory Audit
DIRECTORY            OWNER:GROUP          PERMISSIONS     SIZE
/etc                 root:root            drwxr-xr-x      12M
Example: Log Analysis
Total matches found: 7
Last 5 matching entries:
## Conclusion

This project demonstrates how shell scripting can be used to audit open-source software from both a technical and philosophical perspective, bridging system-level analysis with the core values of open-source development.