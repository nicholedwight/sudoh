---
title: Security+ Study Guide Ch. 1
date: "2020-10-23T22:12:03.284Z"
description: "First chapter of my Security+ Study Guide"
---

<div class="sidebar--wrapper">
<div class="sidebar">
    <a href="#basics">CIA and AAA</a>
    <a href="#use-case">Use Case</a>
    <a href="#confidentiality">Confidentiality</a>
    <a href="#encryption">Encryption</a>
    <a href="#access-controls">Access Controls</a>
    <a href="#steganography">Steganography & Obfuscation</a>
    <a href="#integrity">Integrity</a>
    <a href="#digital-signatures">Digital Signatures</a>
    <a href="#availability">Availability</a>
    <a href="#resourcevssecurity">Resource vs Security Constraints</a>
    <a href="#technical-controls">Technical Controls</a>
    <a href="#administrative-controls">Administrative Controls</a>
    <a href="#operational-controls">Operational Controls</a>
    <a href="#hypervisors">Hypervisors</a>
    <a href="#kali">Kali</a>
</div>
</div>

## Welcome!

This is the first installment of a series I'll be writing for studying for the Security+ exam! Follow along with me in my 'explain it like I'm 5' notes on all the exam objectives! The intent of this series is to help you (and myself) review for the Security+ exam, please don't take these notes as an end-all, be-all. These are just a guide with mildly in-depth discussion of the exam objectives, I highly encourage you to take these notes as a framework for your own further study! Go read up more on everything in here, especially anything you find particularly interesting! (*ahem* steganography anyone?!)

`Note: These posts are in no means meant to be bite-sized content, these will be as detailed and long as I can reasonably make them without writing a whole post on each objective`

Anyway, here we go!


## <span class="result" id="basics">CIA and AAA</span>

I want to begin here because it's absolutely fundamental to understand the concepts here before proceeding to methods and other concepts that protect and uphold CIA. 
#### CIA stands for `Confidentiality`, `Integrity`, and `Availability`.

<span class="pink">- Confidentiality</span> - At its core, confidentiality is all about preventing an unauthorized disclosure of data.

<span class="pink">- Integrity</span> - This refers to our data being unchanged. We know the integrity of our data is good when we can ensure and prove our data has not been changed, modified, or altered in any manner by any unauthorized people. This could occur from unauthorized users, malicious software, and through system and human errors.

<span class="pink">- Availability</span> - Our data and services need to be available whenever access is requested, even if someone is currently attacking! We'll talk more about this in depth soon, but a good way of ensuring availability of data is by making use of redundancy and fault-tolerancy.

#### AAA stands for `Authentication`, `Authorization`, and `Accounting`.

<span class="pink">- Authentication</span> - This is all about the verification of someone's identity. Are you really who you say you are? This happens *all. the. time* in you everyday life, when you login to social media accounts, when you enter your pin at checkout, when you visit a bank, etc. We'll talk a lot more about this soon when we get to digital signatures and the concept of non-repudiation.

<span class="pink">- Authorization</span> - This goes hand-in-hand with authentication, it's generally what follows immediately after authentication, you are given access to the data. Say you are authenticated into your Twitter account, you are then authorized to tweet from that account. If you've ever worked in a fairly commercial building, you have an ID badge which authenticates you as a valid employee, after scanning it you are then authorized access to the rest of the building.

<span class="pink">- Accounting</span> - We're not exactly talking about tracking finances here, but it's a good way to explain the concept! Accounting is just that, taking account or recording everything that has happened on our watch. Think about monitoring logs here. By making use of accounting, we're able to create a good baseline for what ~normal~ activity looks like within our systems.


## <span class="result" id="use-case">Use Case</span>

A `use case` has a few definitions, it describes a goal that an organization wants to achieve, engineers use it in systems analysis and software development to identify and clarify requirements to achieve the goal. Say we're making an online order, "Place Order" would be our use case and it would involve many moving parts! Let's go over the structure of what makes up a use case.

<span class="pink">- Actors</span> - We, or whoever is purchasing this, would be an actor. We might have an account and be a registered user with the website and have our shipping and billing information already inputted into their database. We may be a new customer and our information still needs to be collected. Other actors would include the `billing system` and the `fullfillment system` that processes and ships the order.

<span class="pink">- Precondition</span> - This is something that must occur before the process can start. So we would need to select an item to purchase before we can even place the order.

<span class="pink">- Trigger</span> - This is what will start our use case. So when we click on the shopping cart to begin the purchase process, this action is the trigger.

<span class="pink">- Postcondition</span> - This is what will occur after the actor triggers the process. Our order will be put into the system after we complete our puchase. We'll then receive an acknowledgement of our order, billing may then take additional steps to bill us, and shipping will also take steps to ship us the product.

<span class="pink">- Normal Flow</span> - A use case will typically list each of the steps in a specific order. In our example, we might see a dozen steps that start when we pick an item to order and end when we complete the order and exit the purchasing system or website.

<span class="pink">- Alternate Flow</span> - Not all purchases on this site will be the same. Instead of using existing billing and shipping information, we might want to use a different address or a different credit card than what's already in the system. It's also possible for us to change our mind and abandon the process before completeing the purchase or even cancel *after* we've completed the purchase. 

## <span class="result" id="confidentiality">Confidentiality</span>

Remember just a few minutes ago where we were talking about CIA? Well I wasn't lying when I said it was important! We're going to talk more about confidentiality here. As a recap, at its core, it's about preventing unauthorized disclosure of data. We can ensure the confidentiality of our data by using different methods - `encryption`, `access controls`, `steganography and obfuscation`, and more! 

#### <span id="encryption">Encryption</span>

Encryption scrambles our data so it's no longer readable by unauthorized personnel. For example, you need to transmit Personally Identifiable Information (`PII`), such as medical or credit card information via an email. Once you click send on that email you're no longer in control of that data, hence you'll want to encrypt the email before you send it in order to protect the confidentiality of that data. We'll cover this a lot more in a few more chapters but this is just the base understanding you need for now.

#### <span id="access-controls">Access Controls</span>

Identification, Authentication, and Authorization combined provide access controls and help ensure confidentiality of data. You can use access controls to grant and restrict access to individual people. For example: 

<span class="pink">- Identification</span> - Users claim their identity by using a unique username

<span class="pink">- Authentication</span> - Users then prove their identity with authentication, such as a password

<span class="pink">- Authorization</span> - Then, we're able to either grant or restrict their access to resources using an authorization method, such as permissions.

#### <span id="steganography">Steganography and Obfuscation</span>

`Steganography` is the practice of hiding data within data, otherwise known as hiding data in plain sight. By obscuring the data, it can be used in a use case to support obfuscation (which we'll cover more in depth in another chapter! Again, just the basics here.) `Obfuscation` methods attempt to make something unclear or difficult to understand. We call it 'Security by obscurity', but do keep in mind that this is not a reliable method of maintaining security! Attackers are smart!

You can embed a hidden message in an image by modifying certain bits within the file. If people know what to look for, they'll be able to retrieve the message! Otherwise, they won't be any wiser. Using software like WinRAR you can take a `Cover File` and your `Secret Message` and combine them through a `Steganographic Encoder` which will produce a `Stego Object` which will look *very* similar to your original cover file, with no visible changes, but it will have our secret message embedded! To retrieve the secret message, our Stego Object is then fed into a `Steganographic Decoder`. Does anyone else keep thinking about stegosauruses? 

At this point, you might be wondering how steganography is different from cryptography. Cryptography actually changes the information to ciphertext, modifying the data structure of the original information, which can't be understood without a decryption key. Steganography doesn't change the format of the information, it only conceals the existence of the message within. Steganography is more discreet than cryptography, however, once the existence of the secret message is known it's much easier to extract that information than it would be if it were encrypted with cryptography.

There are so many different kinds of steganography, and I highly encourage you to research them! But one I found really interesting and relevant to the Security+ is `network steganography`. This is the technique of embedding information within network control protocols used in data transmission such as TCP, UDP, ICMP, etc. You can hide information in the header of a TCP/IP packet in some of the optional fields! How cool is that?

Some cool facts about the origination and background of steganography! It stems from two Greek words, `steganos` meaning 'covered' and `graphia` meaning 'writing'. The first use of steganography is traced back to 440 BC when ancient Greece people wrote messages on wood and covered it with wax. Romans used various forms of invisible inks, and in order to decipher those messages they used light or heat. One sehr cool fact is that in WW2 the Germans introduced microdots, which were COMPLETE documents, pictures, or plans reduced to the size of a dot and attached to normal paperwork 🤯

## <span class="result" id="integrity">Integrity</span>

#### <span id="hashing">Hashing</span>

Hashing enforces integrity. This can be done through a few different methods

    - MD5 - Message Digest 5
    - SHA - Secure Hash Algorithm
    - HMAC - Hash-based Message Authentication Code

A `hash` is a number created by executing a hashing algorithm against data, such as a file or message. If the data never changes, the resulting has will ALWAYS be the same. If the hash does not match the source hash or a previous known good hash, it could mean the data has been modified by an attacker, corrupted, or simply updated by a valid source. Hashing cannot tell you what modified the data, only that it has changed, and if it's changed then it implies the data *should not be trusted*. 

## <span class="result" id="digital-signatures">Digital Signatures</span>

Remember, I mentioned we'd be discussing this back in the Authentication section? A lot of things relevant to security will overlap with each other -- just wait until we get into access control classifications! I like to think of the overlap as covering all the gaps, we make sure there isn't a gaping hole in our knowledge we don't know about that attackers could use!

Anyway, digital signatures provies authentication, if the signature is intact, it authenticates the sender. We can use it to prevent attackers from impersonating others and sending malicious emails. This also provides `non-repudiation`, which means someone cannot later deny sending an email for example, because the digital signature proves they did. You can also relate this to audit logs and Linux systems, in each every user is assigned a username and creates their own unique password that no one else should know. This alone with monitoring their activities provides an environment with non-repudiation, if an employee logs into the system and does something nefarious, there's a papertrail to prove it was them!

Digital signatures require the use of certificates and a Public Key Infrastructure (`PKI`). Certificates include keys used for encryption and the PKI provides the means to create, manage, and distribute certificates.

## <span class="result" id="availability">Availability</span>

Recap: Availability means data and services are available whenever needed, even in the middle of an attack. I talked a little before about how redundancy and fault-tolerancy can help ensure availability. Let's go into that a little more

<span class="pink">- Fault-tolerance</span> - If a system has a fault, the duplication provided by redundancy allows that system to continue without interruption. A single fault should not bring down the entire system.

<span class="pink">- Redundancy</span> - this adds duplication to critical systems and provides fault-tolerance. 
    
<div class="indented">

- SPOF - Single point of failure, if this fails, the entire system can fail. For example, if a server has a single drive, the drive is the SPOF because its failure takes down the server. Try to avoid this.

- Disk redundancies - These are fault-tolerant disks such as RAID-1 (mirroring), RAID-5 (striping with parity), and RAID-10 (striping with a mirror) allow a system to continue to operate even if a disk fails.

- Server redundancies - Failover clusters include redundant servers and ensure a service will continue to operate, if with a failure. Virtualization can also increase availability of servers by reducing unplanned downtime.

- Load balancing - uses multiple servers to support a single service, such as a high volume website.

- Site redundancies - If a site can no longer operate to a natural disaster or destruction, the org can move critical systems to an alternate site. Alternate site can be a hot site (ready and available 24/7), a cold site (location where equipment, data, and personnel can be moved to when needed), or a warm site (a compromise between hot and cold sites)

- Backups - If personnel backup important info, it can be restored should originals be lost.

- Alternate power - uninterruptible power supplies (UPSs) and power generators can provide power to key systems 

- Cooling systems - Heating, ventilation, and air conditioning improve the availability of systems by reducing outages from overheating

</div>

## <span class="result" id="resourcevssecurity">Resource vs Security Constraints</span>

![Encrypt All the Data!](./encryptallthedata.jpg)

So, we know encryption is awesome and helps protect the confidentiality of our data. Why not just encrypt ALL THE DATA if that's the best? Well, say we have a message that is 260 characters, after we encrypt it that message would be about 360 characters. That's a 40% increase, which means if we were to encrypt absolutely everything, companies would need to invest in about 40% more disk space to store that encrypted data. Not only that, processing it also consumes more memory. Company executives need to focus on cost of a business, and maintaining profitability. So they need to work with security professionals to find a good common ground and compromise cost and security, it's all about balance. 

## <span class="result" id="risk-concepts">Risk Concepts</span>

`Risk` is the possibility or likelihood of a threat exploiting a vulnerability, resulting in a loss or corruption of data. A `threat` is any circumstance or event that has the potential to compromise confidentiality, integrity, or availability. A `vulnerability` is a weakness, this could be a weakness in the hardware, software, configuration, or even the users' own operating system (`OS`).

If a threat, such as an attacker, exploits a vulnerability, it can result in a security incident. A `security incident` is an adverse event or series of events that can negatively affect the CIA of an organization's IT systems and data.

## <span class="result" id="risk-mitigation">Risk Mitigation</span>

Risk mitigation reduces chances that a threat will exploit a vulnerability. We can reduce risks by implementing controls, also called countermeasures and safeguards.

## <span class="result" id="technical-controls">Technical Controls</span>

These are classified by using technology to reduce vulnerabilities. A few of them include:

    - Encryption
    - Antivirus Software
    - Intrusion Detection Systems (IDSs) and Intrustion Prevention Systems (IPSs)
    - Firewalls
    - Least Privilege - make sure personnel only are given the permissions for what they need to accomplish their jobs, no more!



## <span class="result" id="administrative-controls">Administrative Controls</span>

These use methods mandated by organizational policies or other guidelines. Management may require personnel to periodically complete assessments and tests to reduce and manage risk.

<span class="pink">- Risk assessments</span> - help quantify and qualify risks within an organization, so the organization can focus on the serious risks

<span class="pink">- Vulnerability assessments</span> - attempts to discover current vulnerabilities or weaknesses

<span class="pink">- Penetration tests</span> - this is a step further than vulnerability assessments because in pen tests we also attempt to exploit the vulnerabilities found

## <span class="result" id="operational-controls">Operational Controls</span>

These still fall under administrative controls. Operational Controls help ensure that day-to-day operations of an organization comply with the organization’s overall security plan. People (not technology) then implement these controls.

<span class="pink">- Awareness and training</span>

<span class="pink">- Configuration and change management</span> - configuration management often uses baselines to ensure that systems start in a secure, hardened state. Change management helps ensure that changes don’t result in unintended configuration errors.

<span class="pink">- Contingency planning</span> - goal is to reduce the overall impact on the org if an outage occurs

<span class="pink">- Media protection</span> - media includes physical media such as USB flash drives, external and internal drives, and backup tapes

<span class="pink">- Physical and environmental protection</span>

## <span class="result" id="physical-controls">Physical Controls</span>

These are controls you can *touch*: lighting, signs, fences, cameras, door locks, heating, ventilation systems, security guards, and more. A fire suppression system (and others) are also technical controls, you can physically touch them but they also use technologies to detect, suppress, or extinguish fires.

## <span class="result" id="control-goals">Control Goals</span>

Technical and administrative controls categorize controls based on how they’re implemented. Another way of classifying security controls is based on their goals in relationship to security incidents. Common ones are: 

    - preventative
    - detective
    - corrective
    - deterrent
    - compensating

## <span class="result" id="preventative-controls">Preventative Controls</span>

These are meant to prevent security incidents.

<span class="pink">- Hardening</span> - practice of making a system or application more secure than its default configuration. Uses a defense-in-depth strategy with layered security. Includes disabling unnecessary ports and services, implementing secure protocols, using strong passwords along with a robust password policy, and disabling default and unnecessary accounts. Reduce attack surface!

<span class="pink">- Security awareness and training</span>

<span class="pink">- Security Guards</span>

<span class="pink">- Change management</span> - ensures that changes don’t result in unintended outages. If administrators making changes on the fly, they submit the change to a change management process. This is an operational control, which attempts to prevent incidents.

<span class="pink">- Account disablement policy</span> - ensures user accounts are disabled when an employee leaves.

## <span class="result" id="detective-controls">Detective Controls</span>

These attempt to detect when vulnerabilities have been exploited, resulting in a security incident. 

<span class="pink">- Log monitoring</span>

<span class="pink">- Trend analysis</span> - monitor logs to detect trends. Eg: an intrusion detection system (IDS) attempts to detect attacks and raise alerts or alarms. By analyzing past alerts, you can identify trends, such as an increase of attacks on a specific system

<span class="pink">- Security audit</span> - periodic reviews of password policies, user rights to see if anyone has more permissions than they need, etc.

<span class="pink">- Video surveillance</span> - can also be used as a deterrent control

<span class="pink">- Motion detection</span>

## <span class="result" id="corrective-controls">Corrective Controls</span>

These attempt to reverse the impact of an incident or problem after it has occurred. 

<span class="pink">- IPS</span> - Intrusion prevention system attempts to detect attacks and then modify the environment to block the attack from continuing.

<span class="pink">- Backups and system recovery</span>

## <span class="result" id="deterrent-controls">Deterrent Controls</span>

These attempt to discourage a threat. You can alsodescribe many of them as preventative controls as well.

<span class="pink">- Cable locks</span>

<span class="pink">- Hardware locks</span> - other locks such as locked doors securing a wiring closet or server room

## <span class="result" id="compensating-controls">Compensating Controls</span>

These are alternative controls used instead of a primary control. An org might require employees to use smart cards when authenticating on a system. However, it might take a bit for new employees to get their smart card, to allow them to access the network and still maintain a high level of security, the org might choose to implement a Time-based One-Time Password (`TOTP`) as a compensating control. Compensating controls still provide strong authentication solutions.

## <span class="result" id="hypervisors">Hypervisors</span>

`Virtualization` allows you to host one or more virtual systems, or virtual machines (`VM`) on a single physical system.

A `hypervisor` is the software that creates, runs, and manages the VMs.

<span class="pink">- Type I</span> - run directly on the system hardware, often called bare-metal hypervisors because they don’t need to run within an OS. VMware has a family of ESX/ESXi products that are Type I hypervisors.

<span class="pink">- Type II</span> - run as software within a host OS.

<span class="pink">- Application cell </span>virtualization or container virtualization runs services or applications within isolated application cells (or containers). Containers don’t host an entire OS, instead the host’s OS and kernel run the service or app within each of the containers.

- Container virtualization uses fewer resources and can be more efficient than a system using a traditional Type II hypervisor virtualization. Containers MUST use the OS of the host though

## <span class="result" id="securing-network-architecture">Securing Network Architecture</span>

You can use virtualization as part of an overall secure network architecture. One of the primary benefits is that VMs can provide segregation, segmentation, and isolation of individual systems. One way of doing so is to disable the network interface card (`NIC`) in the VM. This prevents it from transmitting any data in or out of the VM.

<span class="pink">- Snapshot</span> - provides you with a copy of the VM at a moment in time, which you can use as a backup. After taking a snapshot, the hypervisor keeps a record of all changes to the VM. Basically like checkpoints in games! Admins take a snapshot before doing any risky operation like applying patches or updates, testing security controls, and installing new applications. These don’t tend to cause problems, but occasionally they do. An admin can easily revert or roll back the system to a known good state with known good configuration using the snapshot.

## <span class="result" id="vde">VDI/VDE and Non-Persistence</span>

Just how you can virtualize servers, you can also virtualize desktops. In a Virtual Desktop Infrastructure (`VDI`) or a Virtual Desktop Environment (`VDE`), a user’s desktop OS runs as a VM on a server, this is beneficial if a user’s PC has limited hardware resources. 

Some things to consider when running virtual desktops is whether or not they will support persistence or `non-persistence`. In a persistent VD, each user has a custom desktop image, they can customize it and save their data within the desktop. In a non-persistent VD, all users are served the same desktop. When a user accesses the remote server, they’re provided a desktop OS from a preconfigured snapshot. They can make changes as they’re using it, but it reverts to the original snapshot when they log off.

## <span class="result" id="virt-risks">Risks Associated with Virtualization</span>

<span class="pink">- VM Escape</span> - This is an attack that allows an attacker to access the host system from within the virtual system. In some situations, an attacker can run malicious code on the virtual system to be able to interact with the underlying hypervisor. They can also gain access to the host system, which is generally a physical server with elevated privileges, if they get to this point, they will also have access to any other virtual systems on that host.

<span class="pink">- VM Sprawl</span> - This can occur when an organization has many VMs that aren’t managed properly. Let’s say your coworker is spinning up a VM to be able to test some new software, once they’re done they forget about the VM and leave it up and running. Down the line there may be a patch for the OS running on that VM, so IT tests and applies this patch to all of the *known* VMs. But because your coworker didn’t tell anyone about their VM, it’s unpatched and left vulnerable to attack. We also have to think about the additional load to a server if everyone and their gran are spinning up their own VMs, this consumes more system resources, which leads to the servers becoming slower and potentially crashing.

<span class="pink">- Loss of Confidentiality</span> - every VM or virtual system is essentially just one or a collection of files. While this makes them easy to manage and move between physical servers, it also makes them easier to steal. Each VM contains the OS and data, just like a physical system would have both the OS and data on its physical drives. This could include confidential information like a database of financial documents or any proprietary data. Anyone within the company, or even an attacker, could simply make a copy of these files and take them home and launch on another physical server.

## <span class="result" id="kali">✨ Kali ✨</span>

Oh yeah! We’re at some of the fun stuff! Go ahead and download the latest kali iso from (here)[https://www.kali.org/downloads/] and be sure to double check the hash to ensure it wasn’t corrupted during download! Plus it’s good practice 😉 Choose your favorite VM, mine is Oracle VM VirtualBox. We’re going to go over a few command-line tools mentioned in the Security+ objectives that only run within Linux.

#### <span id="switches">Switches</span>

Almost every command has options available that you can call by using a switch. Windows command-line switches use a forward slash (/) or a dash (-). Linux commands use only a dash (-). One of the most useful Windows switches is the `help switch` which is identified with a question mark (?). You can append it to commands in order to get help on how to use them:

    - ping -? Or ping /?
    - ipconfig -? Or ipconfig /?
    - netstat -? netstat /?

Linux has a help feature as well, but it’s not with the ? switch, instead you can just type the command without any switch, or pipe (|) the word help. Or you can use the manpages, manual, for a command, this is typically `man` followed by the command.
    - ping
    - ping | help
    - man ping

Windows is generally not case-sensitive for its commands, but Linux most definitely is. In Linux, commands are typically all lowercase.

#### <span id="ping">Ping</span>

This is a super basic command and it’s widely used to test connectivity for remote systems… or also to check your own internet connection hehe. You can also use it to verify a system can resolve valid host names to IP addresses, test the NIC, and check the security of a network. 

It works by sending Internet Control Message Protocol (ICMP) echo request packets. Remote systems then answer with their own ICMP echo reply packets and if you receive echo recipes, you can know that the remote system is operational. Try it out with `ping google.com`! This is an example of using ping to check name resolution. You can also ping any known IP addresses, press Ctrl+C to cancel the ping, otherwise it’ll forever be sending out packets! If you’re on Windows though, it’ll only send our 4 ICMP echo requests.

#### <span id="firewalls">Firewalls</span>

If your ping receives a reply from a system, you know the other system is operational and reachable. But what if you’re ghosted by that system instead? If your ping fails, it doesn’t necessarily mean the remote system is down, ping might show a “Reply Timed Out” error even if the system is up and functional.

Many denial-of-service (`DoS`) attacks use ICMP to disrupt services on internet-based systems (if you play WoW or any other online game, you’re probably already painfully aware of this concept :( ) Because of this, firewalls commonly block ICMP traffic in order to protect systems and prevent these attacks from happening. You can double check this by going to the website you’re attempting to ping, and if it’s up (it’s operational with HTTP) but your ping command failed, this might be why!

#### <span id="ipconfig">ipconfig, ifconfig, and ip</span>

The `ipconfig` command (Internet Protocol configuration) shows the Transmission Control Protocol/Internet Protocol (`TCP/IP`) configuration for a system. This includes things such as a computer’s IP address, subnet mask, default gateway, MAC address, and the address of a DNS server. It also shows the configuration information for both wired and wireless NICs. It’s commonly used as the first step in troubleshooting network problems.

Linux systems will use `ifconfig` (interface configuration) instead of ipconfig. It has a few extra features that ipconfig doesn’t have. You can use it to configure the NIC as well as listing the properties of the NIC. 

Here are a few common commands, followed by their Linux variations (ifconfig), please look into them!

    - ipconfig Linux: ifconfig
    - ipconfig /all  Linux: ifconfig -a
    - ipconfig /displaydns
    - ipconfig /flushdns
Linux unique commands:

    - ifconfig eth0
    - ifconfig eth0 promisc Disable promiscuous mode with: ifconfig eth0 -promisc
    - ifconfig eth0 allmulti

Normally, an NIC uses non-promiscuous mode and only processes packets that are assigned directly to its IP address. You can put it in promiscuous mode though and it will process all packets regardless of the assigned IP. This allows the protocol analyzer to capture all packets that reach the NIC.

The ifconfig command was deprecated in 2009 in Debian-based distros of Linux, this means that you can still use it, but it’s discouraged, it’s part of a package that is no longer maintained. Instead you can use `ip`! It’s not quite the same, it can still display information and configure network interfaces, but it doesn’t use the same commands/switches or have quite the same abilities. For example, ip doesn’t have a command that allows you to enable promiscuous mode on an NIC.

    - ip link show - shows the interfaces and some info on them
    - ip link set eth0 up - enables a network interface
    - ip -s link - shows statistics on the network interfaces

#### <span id="netstat">Netstat</span>

`netstat` is short for network statistics. It allows you to view statistics for TCP/IP protocols on a system. Many attacks establish connections from an infected computer to a remote computer, if you suspect this may be happening you can often identify the nefarious connections by using netstat.
	
<span class="pink">> netstat</span> - Displays a listing of all open TCP connections 

<span class="pink">> netstat -a</span> - Displays a list of all TCP and User Datagram Protocol (`UDP`) ports that a system is listening on, as well as all open connections. You can use the port number listed to identify protocols, if you see an IP address followed by :80, it indicates the system is listening on the default port of 80 for HTTP (likely a web server)

<span class="pink">> netstat -r</span> - Displays the routing table

<span class="pink">> netstat -e</span> - Displays details on network statistics, like how many bytes the system sent and received.

<span class="pink">> netstat -s</span> - Displays statistics of packets sent or received for specific protocols like IP, ICMP, TCP, and UDP

<span class="pink">> netstat -n</span> - Displays addresses and port numbers in numerical order. Useful if you’re looking for information related to a specific IP or port.

<span class="pink">> netstat -p *protocol*</span> - Shows statistics on a specific protocol like TCP or UDP. netstat -p tcp to show only TCP stats.

You can combine a bunch of the switches for commands to perform multiple operations at once. 
<span class="pink">> netstat -anp tcp</span> - This would show all ports that the system is listening on (-a), in numerical order (-n), for only the TCP protocol (-p tcp)

Netstat displays the state of a connection, such as ESTABLISHED to indicate an active connection. Some more common states are:
    
    - LISTEN - system is waiting for a connection request
    - CLOSE_WAIT - Waiting for a connection termination request
    - TIME_WAIT 
    - SYN_SENT - sent a TCP SYN (synchronize_ packet as first part of SYN-ACK handshake
    - SYN_RECEIVED - sent a TCP SYN-ACK, waiting for ACK response to establish connection.

#### <span id="tracert">Tracert/Traceroute</span>

`tracert` lists the routers between two systems. Each router in this case, is referred to a `hop`. Tracert identifies the IP address and sometimes the host name of each hop as well as the round-trip times (`RTTs`) for each hop. Linux systems use `traceroute`. You can use it to identify faulty routers on the network. If ping fails to reach a distant server, you can use tracert/traceroute to identify where the traffic stops (where the hops fail, packets are being lost). You can also use it to see where the RTTs increase as traffic is routed around a faulty router. 
In a security context, you can use it to identify modified paths. Say our users within an internal network generally access the internet directly by going through router 1, but an attacker has installed an unauthorized router between router 1 and the internet! We can use tracert/traceroute to see this. The attacker can use their router to capture all the traffic passing through with a protocol analyzer and be able to view any data sent in plain text.

`tracert -d` the -d switch forces the command to not resolve IP addresses to host names, which allows it to finish faster.

#### <span id="arp">Arp</span>
Don’t confuse ARP with `arp`! ARP is the Address Resolution Protocol, it resolves IP addresses to MAC addresses and stores the result in the ARP cache. The `arp` command allows you to view and manipulate the ARP cache.

    - arp - shows help on Windows
    - arp - shows the ARP cache on Linux
    - arp -a - shows the ARP cache on Windows
    - arp -a [IP address] - displays the ARP cache entry for the IP address provided 


## <span class="result" id="kali">🥳 Fin! 🎉</span>

You've made it to the end of the first chapter of notes! Congrats! I hope you stick around for the next 10 chapters of my Security+ study guide! This was just a brief overview of a lot of topics we're going to delve more into in the coming posts, keep an eye out!