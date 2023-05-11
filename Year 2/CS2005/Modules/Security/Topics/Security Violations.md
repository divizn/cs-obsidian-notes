
# Contents

[The Security Problem](#the%20security%20problem)
[Types of Security Violation](#types%20of%20security%20violation)
[Typical Security Violation Methods](#typical%20security%20violation%20methods)
[Standard Security Attacks](#Standard%20Security%20Attacks)




# The Security Problem

- A system is secure if its resources are used and accessed as intended under all circumstances.
	- Unfortunately, total security cannot be achieved
	- Security mechanisms can limit security breaches
- Security violations (or misuse) of the system can be categorised as **intentional** (malicious) or **accidental**
- An **attack** is an **attempt** to breach security
- A **threat** is a **potential** security violation, something that may or may not happen, but has the potential to cause serious damage. Threats can lead to attacks on computer devices and networks
- A person who attempts to gain unauthorised access to a system is called an **Intruder**
- An intruder
	- attempts to **damage a system** or **disturb the data** on a system
	- attempts to **violate security**




# Types of Security Violation


### Breach of confidentiality

- Involves unauthorised access to data (or theft of information). For example, credit-card information, identify information (passwords), etc.


### Breach of integrity

- Involved unauthorised modification of data. For example, change the content of a website, change the text of a message, etc.


### Breach of availability

- Involves unauthorised destruction of data. For example, website defacement, wiping data, etc.


### Theft of service

- Involved unauthorised use of resources. For example, an intruder (or intrusion program) may install a daemon on a system that acts as a file server.


### Denial of service

- Involves preventing legitimate use of the system. Denial-of-service (DOS) by overwhelming the service with illegitimate traffic (using bots to stress a server).



# Typical Security Violation Methods


### Masquerading

- One participant in a communication pretends to be someone else (another host or another person).
	- This is a **breach of authentication**, gaining access that would not normally be allowed or obtaining privileges which you would normally not be entitled to.


### Replay attack

- Consists of the malicious or fraudulent repeat of a valid data transmission
- For example, repeat of a request to transfer money, frequently along with **message modification**


### Main-in-the-middle attack

- An attacker sits in the data flow of a communication, masquerading as the sender to the receiver, vice versa.


### Session hijacking

- Intercept an active communication to bypass authentication


# Standard Security Attacks

![stdsec](std-sec-attacks.png)
