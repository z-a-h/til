# Low Level Security 

## Introduction 

Buffer overflows are a type of bug affecting low level code that have serious
security implications. Typically they'll cause a program to crash, but an
attacker can exploit them to steal or corrupt information and run code.

C and C++ are very popular languages and are often used for critical systems
like OS kernels, high-performance servers and embedded systems.
Attacks on these systems can be very dangerous.

Buffer overflow: any access of a buffer outside of its allotted bounds
- over-read or an over-write
- during iteration or direct access
- out-out-bounds access preceding or following the buffer 

More specific terms: 
- buffer underflow: write prior to start
- buffer overread: read past the end
- out of bounds access

### History 

Buffer overflows have a long history. 

The Morris worm was one the first computer worms that spread via the internet in
1988. One of it's propagation techniques was via a buffer overflow attack
against a vulnerable version of `fingerd` on VAXes. It sent a special string to
the finger daemon, causing it to execute code creating a new copy of the worm.
It resulted in over $10M in damages.  Morris is now a prof at MIT.

CodeRed was a 2001 buffer overflow exploit on the MS-IIS server that infected 300,000
machines in 14 hours. It led to Bill Gates calling for Microsoft to increase
their focus on security. 

SQL Slammer was a 2003 MS-SQL exploit that used buffer overflow to infect 75,000
machines in 10 minutes. 


## Memory Layout

## Buffer Overflow

## Code Injection 

## Other Memory Exploits 

## Format String Vulnerabilities 

## Quiz Questions

5. When does a buffer overflow occur, generally speaking?
7. What is a nop sled?
