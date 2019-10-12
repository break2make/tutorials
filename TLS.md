# Does TLS work only on TCP?

Source: https://security.stackexchange.com/questions/170833/why-does-tls-require-tcp

TLS requires a reliable transport. On the internet, this leaves only TCP, as UDP does not offer reliability. 

TLS does require a reliable transport because (in compliance with the layered architecture of the ISO/OSI reference model) it does not handle transport errors, lost packets or other disturbances that may occur with IP.

TLS is designed to offer a secure channel on top of a reliable transport and it does this quite well. DTLS does (I assume) the necessary error handling within the protocol. If TLS was to be performed over UDP, connections and handshakes could fail just because a packet got lost in transit and no one noticed.

Mitigation of such problems is (according to the ISO/OSI reference model) the designated task of a reliable transport. Any reliable transport works theoretically, yet for all practical purposes of IP networks, this usually implies TCP.
