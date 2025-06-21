# CZD Port Scanner 🛠️

![CZD Port Scanner](https://img.shields.io/badge/CZD_Port_Scanner-v1.0.0-blue)

Welcome to the **CZD Port Scanner** repository! This modular and multithreaded port scanning utility is designed to support various scanning techniques, including TCP Connect, TCP SYN (stealth), and UDP probes. It is built for use in internal reconnaissance, network auditing, or red team enumeration phases.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Scanning Techniques](#scanning-techniques)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)
- [Releases](#releases)

## Features 🌟

- **Modular Design**: Easily extend or modify the scanning capabilities.
- **Multithreading**: Perform scans quickly and efficiently.
- **Multiple Protocol Support**: Utilize TCP Connect, TCP SYN, and UDP scanning methods.
- **User-Friendly CLI**: Simple command-line interface for easy interaction.
- **Detailed Reporting**: Get clear and concise results from your scans.

## Installation 🛠️

To get started with CZD Port Scanner, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/vnolxvev/CZD_Port_Scanner.git
   cd CZD_Port_Scanner
   ```

2. **Install Dependencies**:
   Make sure you have Python installed. Then, install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the Scanner**:
   You can start using the scanner right away. Check the usage section for more details.

## Usage 📖

To use the CZD Port Scanner, run the following command in your terminal:

```bash
python scanner.py -h
```

This will display the help message with all available options. You can specify the target IP, port range, and scanning technique.

### Example Command

To perform a TCP SYN scan on a specific IP address, use:

```bash
python scanner.py -t 192.168.1.1 -p 1-1000 -m tcp-syn
```

### Options

- `-t` or `--target`: Specify the target IP address.
- `-p` or `--ports`: Define the port range (e.g., `1-65535`).
- `-m` or `--method`: Choose the scanning method (`tcp-connect`, `tcp-syn`, `udp`).

## Scanning Techniques 🔍

### TCP Connect Scan

This method establishes a full TCP connection with the target. It is straightforward but can be easily detected by firewalls.

### TCP SYN Scan (Stealth)

The TCP SYN scan sends SYN packets and analyzes the responses. It is less likely to be logged by the target, making it stealthier.

### UDP Scanning

UDP scanning checks for open UDP ports. It is more challenging due to the nature of the UDP protocol but essential for a comprehensive scan.

## Contributing 🤝

We welcome contributions to improve the CZD Port Scanner. If you want to contribute, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/YourFeature`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add some feature'`).
5. Push to the branch (`git push origin feature/YourFeature`).
6. Open a pull request.

## License 📄

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact 📬

For any inquiries or issues, please reach out to the maintainer:

- **Name**: Your Name
- **Email**: your.email@example.com

## Releases 📦

To download the latest release of CZD Port Scanner, visit the [Releases](https://github.com/vnolxvev/CZD_Port_Scanner/releases) section. Download the appropriate file and execute it to get started.

You can also check the [Releases](https://github.com/vnolxvev/CZD_Port_Scanner/releases) section for updates and new features.

---

Thank you for your interest in CZD Port Scanner! We hope you find it useful for your network security needs. Happy scanning!