# CTF-Writeup
SickOs1
Use arp-scan to get target's IP 

kwc305:~ KWC$ arp-scan --localnet --interface vmnet8

Interface: vmnet8, datalink type: EN10MB (Ethernet) 

Starting arp-scan 1.9 with 256 hosts (http://www.nta-monitor.com/tools/arp-scan/)

172.16.194.129	00:0c:29:c0:e6:04	VMware, Inc.

172.16.194.130	00:0c:29:27:40:07	VMware, Inc.

172.16.194.254	00:50:56:e8:5c:b2	VMware, Inc.

512 packets received by filter, 0 packets dropped by kernel

Ending arp-scan 1.9: 256 hosts scanned in 1.882 seconds (136.03 hosts/sec). 3 responded




kwc305:~ KWC$ nmap -A -Pn 172.16.194.129

Starting Nmap 6.47 ( http://nmap.org ) at 2016-07-15 23:34 EDT

Nmap scan report for 172.16.194.129

Host is up (0.00066s latency).

Not shown: 997 filtered ports

PORT     STATE  SERVICE    VERSION

22/tcp   open   ssh        OpenSSH 5.9p1 Debian 5ubuntu1.1 (Ubuntu Linux; protocol 2.0)

| ssh-hostkey:

|   1024 09:3d:29:a0:da:48:14:c1:65:14:1e:6a:6c:37:04:09 (DSA)

|   2048 84:63:e9:a8:8e:99:33:48:db:f6:d5:81:ab:f2:08:ec (RSA)

|_  256 51:f6:eb:09:f6:b3:e6:91:ae:36:37:0c:c8:ee:34:27 (ECDSA)

3128/tcp open   http-proxy Squid http proxy 3.1.19

|_http-methods: No Allow or Public header in OPTIONS response (status code 400)

| http-open-proxy: Potentially OPEN proxy.

|_Methods supported:  GET HEAD

|_http-title: ERROR: The requested URL could not be retrieved

8080/tcp closed http-proxy

Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel]

Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .

Nmap done: 1 IP address (1 host up) scanned in 18.38 seconds


Next, we can find port 3128 is Squid proxy server

We can use Firefox and set proxy on target IP and port 3128.

And we can see BLEHHH!!! on website.

Next step, we move to nikto to provide more info.

