# EXPERIMENT 7

Analysis of Application Layer Packets (DNS & HTTP) Using a Packet Tracer Tool (Wireshark) to Understand Their Structure and Working

## THEORY
The Application Layer provides protocols that enable network services and user applications to communicate. **DNS (Domain Name System)** translates human-readable domain names into IP addresses, while **HTTP (Hypertext Transfer Protocol)** manages web resource requests and responses between clients and servers. 

Using command-line lookup utilities along with **Wireshark**, network engineers can capture, filter, and inspect packet headers, query structures, and protocol states.

## TERMINAL SESSION (DNS Lookup)

```cmd
C:\Users\sit.lab2>nslookup [www.google.com](https://www.google.com)
Server:  SIT-CDC.SIT-CDC.SYMBINGP.SOC
Address:  10.17.28.42

Non-authoritative answer:
Name:    [www.google.com](https://www.google.com)
Addresses:  2001:4860:482c:7700::
          2001:4860:4829:7700::
          2001:4860:482b:7700::
          2001:4860:4827:7700::
          2001:4860:482d:7700::
          2001:4860:482a:7700::
          2001:4860:4828:7700::
          142.251.153.119
          142.251.150.119
          142.251.151.119
          142.251.154.119
          142.251.157.119
          142.251.155.119
          142.251.152.119
          142.251.156.119

```

## OBSERVATIONS & WIRESHARK ANALYSIS

1. **DNS Resolution:**
* The `nslookup` query directed to the local server (`10.17.28.42`) successfully mapped `www.google.com` to multiple IPv6 and IPv4 addresses.


2. **Wireshark Packet Inspection:**
* Filtering captured packets revealed standard DNS query/response structures over UDP port 53, showcasing transaction identifiers, query flags, and answer record fields.
* HTTP packet captures further detailed client request headers (`GET`), user agents, server responses (`200 OK`), and payload content length over TCP port 80.


## CONCLUSION

Application-layer packets for DNS and HTTP were successfully analyzed using command-line diagnostic tools and Wireshark. The underlying request-response mechanics, mapping structures, and header configurations were examined and understood.
