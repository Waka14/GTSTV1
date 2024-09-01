# Scanning

- Scanning is the 2nd phase of Ethical Hacking.
- It is the step which helps to test a system based on the information we gathered and also sometime they help as to gather more information's.
- **Scanning** is another essential step, which is necessary, and it refers to the package of techniques or procedures used to identify hosts, ports, and various services within a system

1. **Reconnaissance**: Focuses on broad, high-level information about the target. It may include:
    - Organizational structure and employee details (social engineering possibilities).
    - Publicly available IP addresses and domain names.
    - Technology stack (e.g., web servers, frameworks).
    - Potential entry points from open sources (e.g., website vulnerabilities, exposed subdomains).
2. **Scanning**: Focuses on technical, low-level details about the target’s systems, such as:
    - Open ports and services.
    - Operating system and service versions.
    - Network topology.
    - Specific vulnerabilities in the systems and services.

## why do we do scanning

- It helps to identify HOST's system detail
    - Operation system
    - Service versions
- To discover open ports
- To discover Live systems

### Network scanning

- This is a method of Scanning a network and getting more informations.
- There are Many kinds of scanning methods and tools for different purpose.
    - **For Network mainly**: NMAP,netdiscovery
    - **For Subdomain**: Sublist3r,subfinder,amass
    - **For website**: Nuclei , Nessus, Acunetix..

1. **NMAP**- Network Mapper

- **Nmap** is A network scanning and exploring tool used by network and security experts.
- It is used to scan *Network,Ports,OS*,...
- It is made for windows and linux
- On kali linux it is built in tool.
- To check the existence of nmap on your system
    - nmap --version

### Live system Discovery

- Discovering live system means, Checking up and running hosts(clients/servers) on a network.

### Ping sweep

- This is a method of checking if host is up or down.
- It uses **ICMP**(Internet Control Message Protocol) packets for checking purpose
- It sends **Echo request** and waits for response if there is **Echo reply** then that system is up!
- From echo requests we can gather the following information's
    - OS type
        - Windows ( 32 byte  )
            - ttl=108
        - Linux ( 64 byte )
            - ttl=64
    - Connection stability
        - Time 
- **TTL** : time to live
- it determines how long a packet should exist in the network before being discarded.
    - **Decrementing TTL**: Each time the packet passes through a router (a hop), the TTL value is decreased by 1.
    - **TTL Expiration**: If the TTL reaches 0, the packet is discarded, and an ICMP "Time Exceeded" message is sent back to the sender.

### NMAP ping sweep

- syntax
    - nmap -sn IP  ====> -sn = no port scan

1. **Warning**

- Doing ping sweep is way of Active Recon.
- You are trying to ping the ip.
- And you are trying to do security pentest on my system. And you are script kiddie
- But am a security Guy,so I can see you on my system when you try to do pings on my system. BE SAFE!
- Blue Team Hackers Do this. Like { log analysis, SOC analysis, Intrusion Detection, Incident Response }.

2. **Warning**

- Some Organizations or system admins, will block any **ICMP** requests.
- Here the ping sweep wont work, and when you try this it says “host is down” but it is normally up
- To make it work we just skip Ping requests and ask for additional things
- Syntax: 
    - nmap -Pn IP
- This method will Jump host discovery because it will take the ip as Up and try to do port discoveries.

## Port

- **Port** is process-specific or an application-specific construct serving as a communication endpoint, which is used by the Transport Layer protocols of Internet Protocol suite, such as User Datagram Protocol (UDP) and Transmission Control Protocol (TCP).
- It is like a door for some purpose/service
- On computer there are different **65,536 ports** with different job.
- **1-1024** = reserved(well known) ports
- Example: 
    - HTTP(80) - unsecured Web port
    - HTTPS(443) - secured web port
    - FTP(21) - File transferring port
    - SSH(22) - Secure shell port

### Port status

- Ports can be on different status
    - **Open ports**
        - THESE are ports open for accepting any requests.
    - **Closed ports**
        - THESE are ports which are not accepting any request but there is some service running on it.
    - **Filtered ports**
        - These are ports which nmap is not sure of being open or closed.

#### Open port discovery

- On some system ports can be open for some purpose
- Example: 
    - anywhere when you access websites there is web port open(80,443,8080 mostly), 
    - If you are getting some shell activity there is port 22 open
- The Main problem/Vulnerability is there Might be some ports open without intention or Opened once and forgot closing, this leads to attack.
- We can use nmap to check which port is open/closed And this is called **port discovery**.
- Syntax:
    - nmap IP    =>    only the 1000 ports
    - nmap -p port 1,port2,port3 IP     =>    only    port 1,2,3
    - nmap -p- IP     =>  All the 65K port
- we can use another trick with netcat
    - nc -nv IP port

## Scanning methods

- nmap scans network in different modes
    1. TCP connect(TCP scan)
    2. TCP SYN(stealth scan)
    3. UDP scan
    4. Xmas scan

1. **TCP connect(TCP scan)**

- As we saw last time TCP is the best on doing connection oriented Things. 
- it is reliable But how? Because it uses **3-way HANDSHAKE!!!**
- **3-way handshake**
    - When you establish a TCP connections there is something going behind the scenes
    - What was the packet sent while the Ping sweep, it was the ICMP.
    - Here When we start connection we will send a **Synchronization** flag.
    - When the server got and accepted our request it will reply with **Synchronization and Acknowledgment**.
    - Finally, we will send **Acknowledgement** or **Reset(RST)** and continue because we have connection/network now.
    - TCP scan works like this, so nmap will send the **SYN** request to the ports and if they reply with **SYN/ACK** nmap will reply with **ACK** BOOM!!! That port is open!! Else the port is closed/filtered.
- Syntax:
	- nmap -sT IP

2. **stealth scan**

- This is TCP scan but here we don't send the last **ACK** flag, But we send the **RESET** flag.
- Syntax: 
    - sudo nmap -sS IP

3. **UDP scan**

- This is a method to scan if any service/ port is using UDP.
- It is slow process
- Syntax:
    - sudo nmap -sU IP
- There are some ports work on UDP, SO we need UDP scan.
- SO when you do Pentest do UDP and TCP scans together

4. **Xmas scan**

- Here, The 1st thing to send is FIN/PSH/URG instead of SYN.
- If there is response like **RST** flag Then the system is close.
- If there is no response the system is open.
- Syntax:
    - sudo nmap -sX IP

### Operating system detection

- Nmap have a feature to detect the operating system of the host.
- Syntax:
    - sudo nmap -O IP	=> OS detection only
    - sudo nmap -A IP   => 	OS detection including version  

#### Banner grabbing

- **Banner Grabbing** is a technique of Exfiltrating Version of some Service.
- The "banner" refers to the text or metadata that a service or application sends back when you connect to it, which often contains details about the software, its version, and sometimes even the operating system.

#### scan speeds

- When nmap do its scan, it have a time waiting, after sending 1 packets to a host.
- There are 5 time waitings.
- The nmap time template is -T<0-5>
    - Insane -T5
    - Aggressive -T4
    - Normal -T3
    - Polite -T2
    - Sneaky -T1

#### Nmap insane(T5)

- sending packets insanely fast and waits only **0.3** seconds for the response.
- scan superfast but accuracy is sacrificed sometimes.
- Nmap gives-up on a host if it couldn’t complete the scan within 15 minutes.
- Other than that, -T5 should be used only on a fast network and high-end systems as sending packets this fast can affect the working of the network or system and can result in system failure.
- Syntax:
    - nmap -T5 IP

#### Nmap Aggressive(T4)

- This template is used for sending packets very fast and waits only **1.25** seconds for the response. 
- Nmap official documentation recommends using –T4 for “reasonably modern and reliable networks”.
- Syntax:
	- nmap -T4 IP

#### Nmap normal(T3)

- is a default nmap timing.
- syntax
    - nmap -T3 IP

#### Nmap Polite and Sneaky

- These are the slowest timing.
- Being slow, helps to not be detected on some risky projects.
- Syntax:
	- nmap -T2 IP
	- nmap -T1 IP

### Nmap Script Engine( NSE )

- **Nmap** is capable of running some script on ports and services.
- These scripts are written in lua-programming language.
- These scripts are located in /usr/share/nmap/scripts
- Nmap contains a total number of 589 scripts (Version 7.70), there are a lot of scripts that are useful but not all of them works perfectly, it’s like other tools a better for that particular task, so we’ll look at how we can use the powerful NSE and what scripts to use.
- You can Write your own script too if you can do lua
- Syntax:
    - nmap -sC IP
    - nmap --script scriptname.nse IP
    - Nmap -p 22 –-script ssh* IP 
- you can get in directory in your linux */usr/share/nmap/scripts*.
- Some known scripts.
    - --script banner  =>   grabbing some details
    - --script broadcast  =>  reveals broadcast information
    - --script vuln  =>   test if the ports are vulnerable.

#### Nmap Outputs

- Nmap Can Save your output using the “-oG|-oX|-oN”
    - **-oG** -> For Greppable formats
    - **-oX** -> for xml formats
    - **-oN** -> for Normal Saving Formats

#### Nmap Verbose

- Displaying More Information and Logging them is called Verbose.
- You can also add -v flag to Call verbose
    - **-v** - little detail
    - **-vv** - more detail
    - **-vvv** - much more details

#### Nmap Firewall Evasion

- **Firewall** Evasion Techniques Using Nmap is a subset of network security exploration aimed at bypassing or circumventing firewall protections using the Nmap tool.
- Nmap, known for its versatility in network scanning and reconnaissance, can be leveraged to craft packets in ways that attempt to evade detection by firewalls or intrusion detection systems (IDS).
- IDS (Intrusion Detection System) is a security technology designed to monitor network traffic or system activities for signs of malicious behavior, policy violations, or other unauthorized activities.

## Firewall Evasion Techniques

1. Decoy Scan
2. Fragment packets
3. MAC Address Spoofing
4. Source Port Manipulation

1. **Decoy scan**

- Nmap employs decoy IP addresses to obscure the origin of a scan, complicating the identification of the actual scanner. 
- You can specify multiple decoy IP addresses using the -D option within the Nmap command.
    - nmap -D decoy1, decoy2, decoy3 .... [Target IP]
- You Can Make Nmap to add some random IPs
    - Nmap -D RND:5 … [Target IP]
- This makes it Hard for the sysadmin to block our real ip

2. **Fragment Packets**

- Fragmented requests refer to the technique of sending packets in smaller fragments rather than as whole packets. 
- This is done to evade detection by firewalls, intrusion detection systems (IDS), or intrusion prevention systems (IPS) that rely on analyzing entire packets to detect malicious activity.
- To Perform this:
    - nmap -f -p21 [Target IP]

3. **MAC Address Spoofing**

- This approach can be particularly potent, particularly when a firewall employs MAC filtering to permit communication exclusively from designated MAC addresses.
- By employing a spoofed MAC address, your scan operates stealthily as your genuine MAC address remains concealed in the firewall log files.
- To do this:
    - nmap -spoof-mac *Apple/MAC_ADDRESS* -Pn IP

4. **Source Port Manipulation**

- A common error system admins make is trusting traffic only based on the source port number. 
- DNS may be damaged in particular because UDP DNS responses from external servers can no longer reach the network. 
- Another common example is FTP(21), HTTP(80,8080).
- To do this:
    - nmap -g "PORT" -p 21 IP
