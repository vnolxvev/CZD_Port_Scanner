# CZD PORT SCANNER

A modular, multithreaded Python 3 port scanner built by David Osisek. It supports TCP Connect, TCP SYN (stealth), and UDP scans using raw sockets and Scapy. Designed for internal reconnaissance, firewall validation, and security audits.

- Features
	•	TCP Connect Scan (--scan tcp)
	•	TCP SYN Stealth Scan (--scan syn)
	•	UDP Scan (--scan udp)
	•	Custom Port Ranges (--ports 22,80,443,8000-8010)
	•	Multithreaded for performance
	•	Logs results to port_scanner.log



## - Installation & Setup


## 1. Install Python 3

Make sure Python 3 is installed:

python3 --version

If needed:

sudo apt update && sudo apt install python3 python3-pip -y


## 2. Install Dependencies

Install Scapy for raw packet manipulation:

pip3 install scapy

## - Permissions

SYN and UDP scanning use raw sockets and require root privileges. Always run this tool with sudo:

sudo python3 CZD_Port_Scanner.py ...


## - File Setup

Clone or download this repository and ensure the main script is saved as:

CZD_Port_Scanner.py

## - Usage

Basic Syntax

sudo python3 CZD_Port_Scanner.py --target <ip_or_hostname> --ports <port_list> --scan <tcp|syn|udp>



Examples

TCP Connect Scan

sudo python3 CZD_Port_Scanner.py --target 192.168.1.1 --ports 22,80,443 --scan tcp

SYN Stealth Scan

sudo python3 CZD_Port_Scanner.py --target 192.168.1.1 --ports 1-1024 --scan syn

UDP Scan

sudo python3 CZD_Port_Scanner.py --target 192.168.1.1 --ports 53,123,161,500 --scan udp




## Output 💾 

Scan results are written to:

port_scanner.log

Each entry includes timestamped status information (OPEN, FILTERED, etc.).


### Legal Disclaimer ### 

This tool is for educational and authorized use only. Unauthorized port scanning may violate legal, ethical, or organizational policies. Use responsibly.



Roadmap
	•	Export scan results to JSON or CSV
	•	Add service banner grabbing
	•	CIDR/subnet scanning support
	•	Nmap XML compatibility
	•	OSINT integration support



Author
David Osisek
MIT IT SECURITY, BS Software Dev and Analysis

CZD_Port_Scanner.py is part of a cybersecurity utility suite developed as a showcase of hands-on expertise in Python and network enumeration.



📁 Repo Structure

/CZD_Port_Scanner

├── CZD_Port_Scanner.py

├── README.md

├── port_scanner.log  (auto-generated after scan)

└── /docs              (optional for future documentation)



Questions / Contributions
Feel free to open an issue or submit a pull request for enhancements or fixes.
