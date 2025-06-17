import socket
import threading
import argparse
import logging
from scapy.all import IP, TCP, UDP, ICMP, sr1

### Logging Setup ###
logging.basicConfig(filename="port_scanner.log", filemode='w',
                    format="%(asctime)s - %(levelname)s - %(message)s",
                    level=logging.INFO)

### TCP Connect Scan ###
def tcp_connect_scan(target, port):
    try:
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)
        result = sock.connect_ex((target, port))
        if result == 0:
            msg = f"[TCP] Port {port} is OPEN"
            print(msg)
            logging.info(msg)
        sock.close()
    except Exception as e:
        logging.warning(f"[TCP] Port {port} error: {e}")

### TCP SYN Scan ###
def tcp_syn_scan(target, port):
    try:
        ip = IP(dst=target)
        syn = TCP(dport=port, flags="S")
        resp = sr1(ip/syn, timeout=1, verbose=0)
        if resp and resp.haslayer(TCP) and resp.getlayer(TCP).flags == 0x12:
            msg = f"[SYN] Port {port} is OPEN"
            print(msg)
            logging.info(msg)
            # Send RST to close connection
            rst = TCP(dport=port, flags="R")
            sr1(ip/rst, timeout=1, verbose=0)
    except Exception as e:
        logging.warning(f"[SYN] Port {port} error: {e}")

### UDP Scan ###
def udp_scan(target, port):
    try:
        ip = IP(dst=target)
        udp = UDP(dport=port)
        resp = sr1(ip/udp, timeout=2, verbose=0)
        if not resp:
            msg = f"[UDP] Port {port} is OPEN or FILTERED"
            print(msg)
            logging.info(msg)
        elif resp.haslayer(ICMP):
            if int(resp.getlayer(ICMP).type) == 3 and int(resp.getlayer(ICMP).code) in [1,2,3,9,10,13]:
                msg = f"[UDP] Port {port} is FILTERED"
                print(msg)
                logging.info(msg)
    except Exception as e:
        logging.warning(f"[UDP] Port {port} error: {e}")

### Scan Dispatcher ###
def scan_wrapper(scan_type, target, port):
    if scan_type == "tcp":
        tcp_connect_scan(target, port)
    elif scan_type == "syn":
        tcp_syn_scan(target, port)
    elif scan_type == "udp":
        udp_scan(target, port)

### CLI Parser ###
def parse_ports(port_string):
    ports = set()
    for part in port_string.split(','):
        if '-' in part:
            start, end = map(int, part.split('-'))
            ports.update(range(start, end + 1))
        else:
            ports.add(int(part))
    return sorted(ports)

def main():
    parser = argparse.ArgumentParser(description="Osisek Port Scanner (TCP, SYN, UDP)")
    parser.add_argument("--target", required=True, help="Target IP or hostname")
    parser.add_argument("--ports", default="20-1024", help="Port range (e.g. 22,80,443 or 1-1024)")
    parser.add_argument("--scan", choices=["tcp", "syn", "udp"], required=True, help="Scan type")

    args = parser.parse_args()
    target = args.target
    ports = parse_ports(args.ports)
    scan_type = args.scan

    print(f"\n🔍 Starting {scan_type.upper()} scan on {target}...\n")
    logging.info(f"Started {scan_type.upper()} scan on {target}")

    threads = []
    for port in ports:
        t = threading.Thread(target=scan_wrapper, args=(scan_type, target, port))
        t.start()
        threads.append(t)

    for t in threads:
        t.join()

    print("\n✅ Scan complete. Results saved to 'port_scanner.log'")
    logging.info("Scan complete.")

if __name__ == "__main__":
    main()
