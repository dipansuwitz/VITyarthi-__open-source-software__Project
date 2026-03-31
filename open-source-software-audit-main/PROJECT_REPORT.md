## OPEN SOURCE SOFTWARE ANALYSIS REPORT

## Student Details
Name: Dipansu Bhakat   

Registration Number: 24BAI10759     

Course: Open Source Software (NGMC)

Chosen Software: Mozilla Firefox

Date: 31 March 2026

## AIM

The aim of this project is to conduct a systematic study of Mozilla Firefox as an open-source software system. The analysis includes its background, licensing structure, ethical considerations, and interaction within a Linux environment. Additionally, the project demonstrates practical skills by implementing Bash scripts for automation and system auditing.

## SOFTWARE AND TOOLS USED
Linux environment with Bash shell
Mozilla Firefox (open-source browser)
Standard Linux commands:
hostname, whoami, uname, date, uptime, cat, grep, awk, cut, du, df, ls, tail, read
Package management tools:
dpkg, rpm
## THEORY
Part A — Background and Philosophy
 # A1. Problem Addressed by Firefox

Firefox was developed during a time when web browsing was dominated by a single ecosystem, limiting innovation and reducing adherence to open web standards. This created challenges for developers in terms of compatibility and restricted user awareness regarding privacy and browser behavior.

Mozilla introduced Firefox as an open and standards-compliant alternative. The intention was not only to provide competition but also to ensure that the web remains an open and accessible platform for innovation.

# A2. Licensing and Legal Structure

Firefox is released under the Mozilla Public License 2.0 (MPL 2.0). This license follows a file-level copyleft model, requiring modified files to remain open while allowing integration with differently licensed components.

The four fundamental freedoms of open-source software include:

1.Freedom to use the program
2.Freedom to study the source code
3.Freedom to modify it
4.Freedom to distribute copies

Firefox supports these principles through transparent development and open contribution models.

GPL vs MPL Comparison
GPL v2: Requires all derived works to remain under the same license (strong copyleft)
MPL 2.0: Applies copyleft at file level, allowing flexibility

Context in this project:

GPL is referenced in system-level scripting (Script 1)
Firefox itself uses MPL 2.0

Impact:

GPL ensures strict openness
MPL provides a balance between openness and flexibility
A3. Ethical Aspects of Open Source

Open-source software promotes transparency, collaboration, and accountability. However, it also introduces questions about fair usage, contribution ethics, and commercialization.

Firefox represents a balanced approach by encouraging community contributions while maintaining structured governance.

## Part B — Linux Footprint

Firefox can be installed using package managers like apt, rpm, or dnf. It operates under a normal user account and does not require root privileges for standard usage.

Important components include:

Executable files in system directories
User configuration stored in ~/.mozilla/firefox
Package metadata managed by Linux

Updates are provided through both Mozilla and system repositories.

## Part C — Role in FOSS Ecosystem

Firefox is built on various open-source components and contributes significantly to web standards and privacy features. It serves as a client platform for accessing applications built on open-source infrastructures.

## Part D — Open Source vs Proprietary
Aspect	Open Source (Firefox)	Proprietary Software
Cost	Free	Usually free but controlled
Transparency	High	Limited
Customization	Flexible	Restricted
Support	Community + Organization	Vendor-based
Control	Community-driven	Company-controlled

Conclusion: Firefox is ideal where openness and control are important.

## SCRIPT SUMMARY
1.Script 1: Displays system identity and environment details
2.Script 2: Checks Firefox installation and license
3.Script 3: Audits directory permissions and disk usage
4.Script 4: Analyzes system logs
5.Script 5: Generates an open-source manifesto

## COMMANDS USED
hostname → System name
whoami → Current user
uname → Kernel info
grep, awk, cut → Data processing
du, df → Disk usage
ls -ld → Permissions
tail → Log output
read → Input

## ALGORITHM

Select Firefox

Implement Script 1
Implement Script 2
Implement Script 3
Implement Script 4
Implement Script 5
Execute and verify outputs
PROGRAM
Script 1 (script1.sh)
#!/bin/bash

# Script 1: System Identity Report

if [ -f /etc/os-release ]; then
    OS_NAME=$(grep '^PRETTY_NAME=' /etc/os-release | cut -d'=' -f2- | tr -d '"')
else
    OS_NAME="$(uname -s) $(uname -m)"
fi

if uptime -p >/dev/null 2>&1; then
    SYSTEM_UPTIME=$(uptime -p)
else
    SYSTEM_UPTIME=$(uptime | sed 's/.*up \([^,]*\).*/\1/')
fi

echo "========================================="
echo "       SYSTEM IDENTITY REPORT"
echo "========================================="

echo "Hostname: $(hostname)"
echo "Logged in user: $(whoami)"
echo "Home directory: $HOME"

echo "Operating System Details:"
echo "$OS_NAME"

echo "Kernel Version: $(uname -r)"

echo "System Uptime: $SYSTEM_UPTIME"

echo "Current Date and Time: $(date)"

echo "Open Source License: GNU General Public License v2"
echo "========================================="
Script 2 (script2.sh)
#!/bin/bash

# Script 2: FOSS Package Inspector

echo "========================================="
echo "       FOSS PACKAGE INSPECTOR"
echo "========================================="

PACKAGE="firefox"
PKG_MANAGER="unknown"

if command -v rpm &>/dev/null; then
    PKG_MANAGER="rpm"
elif command -v dpkg &>/dev/null; then
    PKG_MANAGER="dpkg"
fi

if [ "$PKG_MANAGER" = "rpm" ]; then
    if rpm -q "$PACKAGE" &>/dev/null; then
        echo "$PACKAGE is installed"
        rpm -qi "$PACKAGE" | grep -E 'Version|License|Summary'
    else
        echo "$PACKAGE not installed"
    fi

elif [ "$PKG_MANAGER" = "dpkg" ]; then
    if dpkg -l | grep -qw "$PACKAGE"; then
        echo "$PACKAGE is installed"
        dpkg -l | grep -w "$PACKAGE"
        "$PACKAGE" --version
    else
        echo "$PACKAGE not installed"
    fi
fi

echo "License: MPL 2.0"

## Script 3 (script3.sh)
#!/bin/bash

printf "%-20s %-20s %-12s %-12s\n" "DIRECTORY" "OWNER:GROUP" "PERMS" "SIZE"

for DIR in /etc /var/log /home /usr/bin /tmp
do
    if [ -d "$DIR" ]; then
        OWNER=$(ls -ld "$DIR" | awk '{print $3":"$4}')
        PERMS=$(ls -ld "$DIR" | awk '{print $1}')
        SIZE=$(du -sh "$DIR" 2>/dev/null | cut -f1)

        printf "%-20s %-20s %-12s %-12s\n" "$DIR" "$OWNER" "$PERMS" "$SIZE"
    fi
done

## Script 4 (script4.sh)
#!/bin/bash

  LOGFILE="/var/log/syslog"
  KEYWORD="error"
  COUNT=0

   while read LINE
    do
    echo "$LINE" | grep -i "$KEYWORD" >/dev/null
    if [ $? -eq 0 ]; then
        COUNT=$((COUNT+1))
      fi
     done < "$LOGFILE"

echo "Total matches found: $COUNT"
echo "Last 5 matching lines:"
grep -i "$KEYWORD" "$LOGFILE" | tail -5

## Script 5 (script5.sh)
#!/bin/bash

read -p "Tool: " TOOL
read -p "Freedom word: " FREEDOM
read -p "Build idea: " BUILD

echo "I use $TOOL daily."
echo "Freedom means $FREEDOM."
echo "I will build $BUILD."

## OUTPUT
Sample Output

Script 1

Hostname: ubuntu
Kernel Version: 5.15.0

Script 2

       FOSS PACKAGE INSPECTOR


firefox is installed
ii  firefox   123.0+build1   amd64   Mozilla Firefox web browser
Mozilla Firefox 123.0

License: MPL 2.0

Script 3

DIRECTORY            OWNER:GROUP          PERMS        SIZE
/etc                 root:root            drwxr-xr-x   12M

Script 4

Total matches found: 7
Last 5 matching lines:

Script 5
Tool: firefox
Freedom word: sharing
Build idea: open source app

I use firefox daily.
Freedom means sharing.
I will build open source app.


## OBSERVATION
Script 1 identifies system details
Script 2 verifies package installation
Script 3 shows permission structure
Script 4 analyzes logs
Script 5 generates output based on input

## RESULT

The project successfully demonstrates the analysis of an open-source system along with practical implementation through scripting. It clearly explains licensing differences, system interaction, and automation tasks, fulfilling all required objectives.
