## Network Security Interview Question
________
## [Network Security Concept]
### 1. What is Network Security?
Network security is the security provided to a network from unauthorized access and risks. It is the duty of network administrators to adopt preventive measures to protect their networks from potential security threats.

### 2. Types of Network Security?
* Antivirus and Antimalware Software: is a software program that protects a computer from any malicious software, any virus, spyware, adware, etc.
* Application Security
* Behavioral Analytics
* Data Loss Prevention (DLP)
* Email Security
* **Firewalls**: acts as a gatekeeper which prevents unauthorized users to access the private networks as intranets.
* Mobile Device Security
* Network Segmentation
* Security Information and Event Management (SIEM)
* **Virtual Private Network (VPN)**
* Web Security
* Wireless Security
* Endpoint Security
* Network Access Control (NAC)

### 3. What is Data encryption?
- Data encryption ensures data safety and very important for confidential or critical data.
- It protects data from being read, altered or forged while transmission.
- It changes the electronic information into an unreadable state by using algorithms or ciphers.
- Web browsers automatically encrypt the text when they are connected to a secure server.
- In the olden days data encryption was only used for passing government and military information.

### 4. What is the Public Key Encryption?
Public key encryption use public and private key for encryption and decryption. In this mechanism, public key is used to encrypt messages and only the corresponding private key can be used to decrypt them. To encrypt a message, a sender has to know recipient’s public key.

### 5. How do you define risk, vulnerability, and threat, in the context of network security?
A risk is defined as the result of a system being secure but not secured sufficiently, thereby increasing the likelihood of a threat. A vulnerability is a weakness or breach in your network or equipment (e.g. modems, routers, access points). A threat is the actual means of causing an incident; for instance, a virus attack is deemed a threat.

### 6. What are the possible results of an attack on a computer network?
Possible results include:
Loss or corruption of sensitive data that is essential for a company’s survival and success
Diminished reputation and trust among customers
The decline in value with shareholders
Reduced brand value
Reduction in profits

### 7. Explain the difference between symmetric and asymmetric encryption.
Long story short, symmetric encryption uses the same key for both encryption and decryption, whereas asymmetric encryption employs different keys for the two processes. Symmetric is faster for obvious reasons but requires sending the key through an unencrypted channel, which is a risk.

### 8. Explain the difference between a white and black hat hacker.
Black and white hat hackers are different sides of the same coin. Both groups are skilled and talented in gaining entry into networks and accessing otherwise protected data. However, black hats are motivated by political agendas, personal greed, or malice, whereas white hats strive to foil the former. Many white hats also conduct tests and practice runs on network systems, to ascertain the effectiveness of security.
________
## [Firewall]
The network firewall is considered as the first line of defense against any cyber attack. It is able to protect different servers based on the firewall configuration.
### 1. What is Network Firewall?
A firewall is a hardware or software installed to provide security to the private networks connected to the internet. They can be implemented in both hardware and software, or a combination of both. All data entering or leaving the Intranet passes through the firewall which allows only the data meeting the administrators’ rules to pass through it.

### 2. What Are The Types Of Firewalls?
* **Packet Filtering Firewall**: This type of Firewall detects packets and block unnecessary packets and makes network traffic release.
* **Screening Router Firewalls**: It's a software base firewall available in Router provides only light filtering.
* **Computer-based Firewall**: It's a firewall stored in server with an existing Operating System like Windows and UNIX.
* **Hardware base Firewall**: Its device like box allows strong security from public network. Mostly used by big networks.
* **Proxy Server**: Proxy server allows all clients to access Internet with different access limits. Proxy server has its own firewall which filters the all packet from web server.
 
 ### 3. Digital Signatures?
 * Digital signature is an attachment to an electronic message used for security purpose. 
 * It is used to verify the authenticity of the sender.
 * It is also known as a mathematical technique which is used to validate the authenticity and integrity of a message software or a digital document.
 * They provide assurance of evidence of originality identity and status of an electronic document transaction or message and even acknowledges the informed consent of the signer.
 * It has a legal significance.
 
 ### 4. Firewalls Works At Which Layers? Define firewall generations and their roles.
  * Firewalls work at layer 3, 4 & 7. 
  * First generation firewalls provide packet filtering and they generally operate at layer 3 (Network Layer). 
  * Second generation firewalls operate up to the Transport layer (layer 4) and records all connections passing through it and determines whether a packet is the start of a new connection, a part of an existing connection, or not part of any connection. Second generation firewall is mainly used for Stateful Inspection.
 * Third generation firewalls operate at layer 7. The key benefit of application layer filtering is that it can “understand” certain applications and protocols (such as File Transfer Protocol (FTP), Domain Name System (DNS), or Hypertext Transfer Protocol (HTTP)).
 
 ### 5. What is Authorization?
 Authorization is a security mechanism used to determine user/client privileges or access levels related to network resources, including firewalls, routers, switches and application features. Authorization is normally preceded by authentication and during authorization. It’s system that verifies an authenticated user’s access rules and either grants or refuses resource access.
 
 ### 6. What Is Log Processing?
 How audit logs are processed, searched for key events, or summarized.

______
## [VPN]
A VPN is another type of network security capable of encrypting the connection from an endpoint to a network, mostly over the Internet. A remote-access VPN typically uses IPsec or Secure Sockets Layer in order to authenticate the communication between network and device.

### 1. What is VPN and describe IPsec VPN
* Virtual Private Network (VPN) creates a secure network connection over a public network such as the internet.
* IPsec VPN means VPN over IP Security allows two or more users to communicate in a secure manner by authenticating and encrypting each IP packet of a communication session.

### 2. Types of VPN?
* Site to Site VPN: 
* Remote access VPN: 
A site-to-site VPN allows offices in multiple locations to establish secure connections with each other over a public network such as the Internet. Site-to-site VPN is different from remote-access VPN as it eliminates the need for each computer to run VPN client software as if it were on a remote-access VPN.

### 3. What is DoS attack? How can it be prevented?
DoS (Denial of Service) attack can be generated by sending a flood of data or requests to a target system resulting in a consume/crash of the target system’s resources. The attacker often uses ip spoofing to conceal his identity when launching a DoS attack.

______
## [Basic Network Attacks]
### 1. Virus
A virus is not self-executable; it requires the user’s interaction to infects a computer and spread on the network. An example is an email with a malicious link or malicious attachment. When a recipient opens the attachment or clicks the link, the malicious code gets activated and circumvents the systems security controls and makes they inoperable. In this case, the user inadvertently corrupts the device.

### 2. Malware
Malware attack is one of the most severe cyberattacks that is specifically designed to destroy or gain unauthorized access over a targeted computer system. Most malware is self-replicating, i.e., when it infects a particular system, it gains entry over the internet and from thereon, infects all the systems connected to the internet in the network. An external endpoint device if connected, will also get infected. It works exceptionally faster than other types of malicious content.

### 3. Worm
A worm can enter a device without the help of the user. When a user runs a vulnerable network application, an attacker on the same internet connection can send malware to that application. The application may accept the malware from the internet and execute it, thereby creating a worm.

### 4. Phishing
Phishing is the most common types of network attacks. It stands for sending emails purporting as from known resources or bankers and creating a sense of urgency to excite user to act on it. The email may contain malicious link or attachment or may ask to share confidential information.

### 5. Botnet
It is a network of private computers which are a victim of malicious software. The attacker controls all the computers on the network without the owner’s knowledge. Each computer on the network is considered as zombies as they serve the purpose of spreading and infecting a large number of devices or as guided by the attacker.

### 6. DoS (Denial of Service)
A Denial of Service is a crucial attack that destroys fully or partially, victim’s network or the entire IT infrastructure to make it unavailable to the legitimate users.
* The DoS attacks can be categorized in the following three parts –
    * **Connection flooding:** The attacker bogs down the host by establishing a large number of TCP connections at the targeted host. These fake connections block the network and make it unavailable to legitimate users.
    * **Vulnerability attack:** By sending a few well-crafted messages to the vulnerable operating system or application running on the targeted host, stops the service or make it worse to the extent that the host crashes.
    * **Bandwidth flooding:** The attacker prevents legitimate packets from reaching the server by sending a deluge of packets. The packets sent are large in number so that the target’s link gets blocked for others to access.

### 7. Distributed Denial of Service (DDoS)
It is a complex version of a DoS attack and is much harder to detect and defend compared to a DoS attack. In this attack, the attacker uses multiple compromised systems to target a single DoS attack targeted system. The DDoS attack also leverages botnets.

### 8. Man-in-the-middle
A man-in-the-middle attack is someone who stands in between the conversation happening between you and the other person. By being in the middle, the attacker captures, monitors, and controls your communication effectively. For example, when the lower layer of the network sends information, the computers in the layer may not be able to determine the recipient with which they are exchanging information.

### 9. Packet Sniffer
When a passive receiver placed in the territory of the wireless transmitter, it records a copy of every packet transmitted. These packets can contain confidential information, sensitive and crucial data, trade secrets, etc. which when flew over a packet receiver will get through it. The packet receiver will then work as a packet sniffer, sniffing all the transmitted packets entering the range. The best defense against packet sniffer is cryptography.

### 10. DNS Spoofing
It is about compromising a computer by corrupting domain name system (DNS) data and then introducing in the resolver’s cache. This causes the name server to return an incorrect IP address.

### 11. IP Spoofing
It is the process of injecting packets in the internet using a false source address and is one of the ways to masquerade as another user. An end-point authentication that ensures the certainty of a message originating from the place we determined would help in defending from IP spoofing.
* What is IP Spoofing?
    * An IP spoofing attack enables an attacker to replace its identity as trusted for attacking host. For example, if an attacker convinces a host that he is a trusted client, he might gain privileged access to a host.
    * An attack whereby a system attempts to illicitly impersonate another system by using its IP network address.
    * In computer networking, the term IP address spoofing or IP spoofing refers to the creation of Internet Protocol (IP) packets with a forged source IP address, called spoofing, with the purpose of concealing the identity of the sender or impersonating another computing system

### 12. Compromised Key
An attacker gains unauthorized access to a secured communication using a compromised key. A key refers to a secret number or code required to interpret secured information without any intimation to the sender or receiver. When the key is obtained by the attacker, it is referred to as a compromised key which serves as a tool to retrieve information.
