Assignment 3

Ashish Kumar
1590883

Task 1:
Q.1. What is the output of nodes and net?
Ans. 
nodes :
available nodes are:
h1 h2 h3 h4 h5 h6 h7 h8 s1 s2 s3 s4 s5 s6 s7

net :
h1 h1-eth0:s3-eth1
h2 h2-eth0:s3-eth2
h3 h3-eth0:s4-eth1
h4 h4-eth0: s4-eth2
h5 h5-eth0:s6-eth1
ho ho-eth0:s6-eth2
h7 h7-eth0:s7-eth1
h8 h8-eth0:s7-eth2
s1 lo: s1-eth1:s2-eth3 s1-eth2:s5-eth3
s2 lo: s2-eth1:s3-eth3 s2-eth2:s4-eth3 s2-eth3:s1-eth1
s3 lo: s3-eth1:h1-etho s3-eth2:h2-eth0 s3-eth3:s2-eth1
s4 lo: s4-eth1:h3-etho s4-eth2:h4-eth0 s4-eth3:s2-eth2
s5 lo: 55-eth1:s6-eth3 s5-eth2:s7-eth3 s5-eth3:s1-eth2
s6 lo: s6-eth1:h5-etho s6-eth2:h6-eth0 s6-eth3:s5-eth1
s7 lo: s7-eth1:h7-etho s7-eth2:h8-eth0 s7-eth3:s5-eth2

Q.2. What is the output of “h7 ifconfig?
Ans. h7-etho: flags=4163<UP, BROADCAST, RUNNING, MULTICAST> mtu 1500
net 10.0.0.7 netmask 255.0.0.0 broadcast 10.255.255.255
inet6 fe80::14ad:cbff:fe1f:5616 prefixlen 64 scopeid 0x20<link>
ether 06:ad:cb:18:56:16 txqueuelen 1000 (Ethernet)
RX packets 231 bytes 25094 (25.0 KB)
RX errors 0 dropped 0 overruns frame 0
TX packets 11 bytes 866 (866.0 B)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions o
lo: flags=73<UP, LOOPBACK, RUNNING> mtu 65536
inet 127.0.0.1 netmask 255.0.0.0
inet6 ::1 prefixlen 128 scopeid 0x10<host>
loop txqueuelen 1000 (Local Loopback)
RX packets bytes 0 (0.0 B)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 0 bytes 0 (0.0 B)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0




Task 2:
Q.1. Draw the function call graph of this controller. 
Ans. _handle_PacketIn -> act_like_hub -> resend_packet

Q.2. Have h1 ping h2, and h1 ping h8 for 100 times.
a. How long does it take (on average) to ping for each case? 
Ans. For h1 and h2, it takes 1.858 ms and for h1 and h8, it takes 12.022 ms

b. What is the minimum and maximum ping you have observed? 
Ans. For h1 and h2, minimum was 1.157 ms and maximum was 3.612 ms. For h1 and h8, minimum was 6.452 ms and maximum was 21.183 ms. 

c. What is the difference, and why?
Ans. The latency is lower in case of h1 and h2 because they’re connected to the same switch so the data transfer is very fast while there are five switches in the shortest path between h1 and h8 so data takes longer to be transferred between them.

Q.3. 
a. What is “iperf” used for?
Ans. iperf is used to estimate the maximum achievable bandwidth on IP networks.

b. What is the throughput for each case?
Ans. for h1 and h2 it is 9.64Mbits/sec and for h1 and h8, it is 2.86Mbits/sec.

c. What is the difference, and explain the reasons for the difference.
Ans. The throughput for h1 and h2 is much higher than h1 and h8’s, because as described in the question 2 above, the latency is much lower for h1 and h2 compared to h1 and h8, and throughput is generally inversely proportional to latency. 



Task 3:
Q.1. Describe how the above code works.
Ans. It first tries to learn the source ports of the data packets. After receiving a packet, it tries to find its destination address. If it is known, the packet is forwarded to that port, otherwise it acts like a hub and sends the packet to all the ports (flooding).

Q.2. Have h1 ping h2, and h1 ping h8 for 100 times (e.g., h1 ping -c100 p2). 
a. How long did it take (on average) to ping for each case? 
Ans. For h1 and h2, it takes 0.087 ms and for h1 and h8, it takes 0.113 ms

b. What is the minimum and maximum ping you have observed? 
Ans. For h1 and h2, minimum was 0.06 ms and maximum was 0.403 ms. For h1 and h8, minimum was 0.081 ms and maximum was 0.407 ms.

c. Any difference from Task 2 and why do you think there is a change if there is? 
Ans. The latency in this case is much lower because we are using a switch here instead of a hub. A switch reduces collisions/retransmissions and sends traffic only to the destination device, thereby increasing data transfer speeds and decreasing latency.


Q.3 Run “iperf h1 h2” and “iperf h1 h8”.
a. What is the throughput for each case? 
Ans. for h1 and h2 it is 16.3 Gbits/sec and for h1 and h8, it is 17.5Gbits/sec.

b. What is the difference from Task 2 and why do you think there is a change if there is?
Ans. The throughput here, when we are using switches, is much higher than the throughput when using hubs. This is because switches send traffic only to the destination port, while hubs broadcast the data to all ports. So a switch provides more reliable and faster transfers of data. The difference between hub and switch transfer speeds becomes more noticeable as more devices are added to the network.

