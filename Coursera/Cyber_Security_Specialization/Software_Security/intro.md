# Week 1

Most developers and operators are concerned with correctness.
Security is concerned with preventing undesired behavior.

Kinds of Undesired Behavior
- Confidentiality: Steal Information
- Integrity: Modify Information of Functionality
- Availability: Denying Access

Many breaches begin by exploiting a vulnerability. 
Vulnerabilities are security-relevant software defects that can be exploited to
effect an undesired behavior.

A software defect is present when the software behaves incorrectly.

Defects can occur in the design and implementation of software.
- A flaw is a defect in the design
- a bug is a defect in the implementation

When considering defects from the point of view of security, it's not sufficient
to judge the importance of bugs with respect to typical use cases. Developers
must consider atypical misuse cases, because an adversary is not a typical user.

An adversary will actively attempt to find defects to exploit them. 


## Software Security

A branch of security that focuses on the secure design and implementation of
software.
Software defects are often the root cause of many exploits and

### Operating System Security 

Operating Systems mediate program's actions (system calls)
Enforceable polices control actions

*Limitations of OS Security*
Cannot enforce application-specific policies, which can be too fined-grained
  - Example: Database Management System
Cannot (precisely) enforce info-flow polices
  - OS's typically implement an execution monitor: decisions are based on past
    and current actions
  - Information flow policies: A non-action may reveal something about a secret
    without leaking it directly.

### Firewalls and Intrusion Detection Systems 

Firewalls and IDS observe, block and filter messages.
- Firewalls block all traffic from particular hosts or to particular ports
- IDS can filter packets it recognizes are part of a known exploit pattern

Firewall filtering is coarse-grained and unsound 
-  Port 80 is assumed to be HTTP traffic, but can layer arbitrary traffic over
   HTTP (e.g. SOAP)

IDS patterns fine-grained, but still unsound
- Attack traffic can be slightly modified to work around IDS filters
- Making filters too fined grained can hut performance (thus compromising
  availability)

### Anti-Virus Scanners 

Look for signs of malicious behavior in local files. 
Similar to IDS in looking for patterns. 
Newer forms of anti-virus scanners are sophisticated but in practice are
frequently bypassed. 
Trade off precision and performance, which can impact availability.


