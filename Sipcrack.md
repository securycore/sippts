Sipcrack is a remote password cracker. Sipcrack uses multithread and using a wordlist can test passwords for several users in IP and port ranges.

# Features #
Sipcrack allows us to:
  * Test remotely a list of users and passwords using REGISTER method
  * Test users and passwords on a network range
  * Use a prefix for extensions range (maybe user and extension is not the same)
  * Connect over UDP or TCP protocol.
  * Try UDP and TCP at the same time.
  * Resume a previous session
  * Analyze responses using verbose mode.

# Usage #
```
$ perl sipcrack.pl

SipCRACK - by Pepelux <pepeluxx@gmail.com>
--------

Usage: perl sipcrack.pl -h <host> -w wordlist [options]
 
== Options ==
-e  <string>     = Extension (default from 100 to 1000)
-s  <integer>    = Source number (CallerID) (default: 100)
-d  <integer>    = Destination number (default: 100)
-r  <integer>    = Remote port (default: 5060)
-p  <string>     = Prefix (for extensions)
-proto  <string>  = Protocol (UDP or TCP - By default: UDP)
-ip <string>     = Source IP (by default it is the same as host)
-resume          = Resume last session
-w               = Wordlist
-v               = Verbose (trace information)
-vv              = More verbose (more detailed trace)
```

  * Try to crack extensions from 100 to 1000 on 192.168.0.1 port 5060
```
perl sipcrack.pl -h 192.168.0.1 -w wordlist
```

  * Try to crack extensions from user100 to user200 on 192.168.0.0 network
```
perl sipcrack.pl -h 192.168.0.0/24 -e 100-200 -p user -w wordlist
```

# Example #
```
$ perl sipcrack.pl -h 192.168.0.55 -e 100-200 -w dictionary
Found match: 192.168.0.55:5060 - User: 100 - Pass: p3p3lux
Found match: 192.168.0.55:5060 - User: 101 - Pass: p3p3lux

IP address	Port	Exten	Pass
==========	====	=====	====
192.168.0.55	5060	100	p3p3lux
192.168.0.55	5060	101	p3p3lux
```