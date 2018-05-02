## Networking and Tools

Notes and useful bits taken whilst practing networking.

* [Udacity Networking course](https://classroom.udacity.com/courses/ud256/)

## Setup and installs

Setup a local linux box

* [Virtual Box](https://www.virtualbox.org/wiki/Downloads) 
* [Vagrant](https://www.vagrantup.com/downloads.html)

Setup a linux box in [Amazon](https://aws.amazon.com/lightsail/)

Run shell add-ons

* `sudo apt-get install netcat-openbsd tcpdump traceroute mtr`

## Ping to HTTP

`nc` is a utiliy to read or write to network connections using TCP or UDP.

Scan domain for open ports succeed

`netcat -z -v domain.com 1-1000 | grep succeeded`

`nc -l 2345`

( you can run in browser <ip_address:port> to see HTTP request info in shell )

## Names and Addressess

`ping` and `echo`requests - can machines talk via a network ( not HTTP specific )

`host` is a utility to look up DNS to IP

DNS, A MX C records

IP addresses | Port numbers | Bytes

## Names and Addressess

IPv4 = 32-bits 4 octet

Reserved IPs

Network blocks ( 198.51.100.17 & 198.51.100.143 )

Subnet masks ( e.g. 24 network = 255.255.255.0, 16 network 255.255.0.0 )

IP address belong to network interfaces `ip addr show`
* Ethernet | Wifi | LoopBack | Tunnel

`ip addr show eth0`

`ip route show`

`ifconfig | less`

Routers and Default Gateways

Home routes user NAT ( network address translation, router re-writes )
* inside_address:port != outside_address:port

Private and Public IPs, and IPv6

* `ip route show default` ( linux only )
* `netstat -nr` ( all )

## Protocol Layers

HTTP on TCP on IP on hardware ( protocol stack )

Layer / Protocol / Concepts

Application / Transport / Internet / Hardware

HTTP / TCP / IP / WiFi

Network Protocols - what is happening when a TCP connections opens?
* two endpoints get into agreement a connection exists
* client sends servers IP and port number
* TCP uses sequencing to send packets of data and receives and ACK each time client receives a data packet

TCP connections initiate via a three-way handshake using `SYN` flag `S`

If accepts server replies via a `S` and `ACK` flag.

TCP uses a four way tear down using flags `F` and `ACK`

ICMP and UDP do not have TCP flags:
* If you look at tcpdump data for pings or basic DNS lookups, you will not see flags. This is because ping uses ICMP, and basic DNS lookups use UDP. These protocols do not have TCP flags or sequence numbers.
* TCP congestion control is one of most important performance features of TCP.

`sudo tcpdump -n -c5 -i eth0 port 22`

`sudo tcpdump -i en0`

`sudo tcpdump -D`

`sudo tcpdump -n host 8.8.8.8`

`sudo tcpdump -n <host> port 53 ( DNS )`

`sudo tcpdump -n <host> port 22 ( SSH )`

`sudo tcpdump -n <host> port 80 ( Internet )`

## Useful script commands

`man nc`

`nc -l port` 

`nc 0.0.0.0 3456`

`nc -l 4444 | tar xzvf -`

`tar -czf - * | nc domain.com 4444`

`sudo lsof -i`

`host 0.0.0.0`

`host -t a 0.0.0.0`

`host -t mx 0.0.0.0`

`dig 0.0.0.0`

`scp -i private-key.ext Desktop/path_to_file.ext bitnami@1.2.3.4:~`

`ip addr show eth0`

`ip route show`

`ifconfig | less`

`tcpdump -n -c5 -i eth0 port 22`

`sudo tcpdump -i en0`

`sudo tcpdump -D`

`networksetup -listallhardwareports`

`traceroute www.google.com`

`ip route show default`

`netstat -nr`

`sudo tcpdump -n host 8.8.8.8`

`sudo tcpdump -n <host> port 80 ( Internet )`

`printf ‘HEAD / HTTP/1.1\r\nHost: example.net\r\n\r\n’ | nc example.net 80`

`printf "GET / HTTP/1.1\r\nHost: www.example.com\r\n\r\n" | nc www.example.com 80 > example.txt`

## Holder

*blank text*

Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.
