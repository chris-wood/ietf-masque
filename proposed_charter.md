Many network topologies lead to situations where transport protocol proxying is
beneficial. For example, proxying enables endpoints to communicate when
end-to-end connectivity is not possible and can apply additional encryption
where desirable (such as a VPN). Proxying can also improve client privacy, e.g.,
by hiding a client's IP address from a target server.

Proxying technologies such as SOCKS and HTTP(S) CONNECT exist, albeit with their
own shortcomings. For example, SOCKS signalling is not encrypted and HTTP
CONNECT is currently limited to TCP. In contrast, HTTP/3 is a viable candidate
protocol for proxying arbitrary traffic, as it provides secure connectivity,
multiplexed streams, and migration for a single connection while taking
advantage of a unified congestion controller. An HTTP/3 datagram construct built
on top of QUIC datagram frames would provide for unreliable data transmission
and enable transporting UDP and other unreliable flows via a proxy. Moreover, it
would not introduce potentially redundant or unnecessary recovery mechanisms.
Lastly, HTTP supports an established request/response semantic that can set up
and configure flows for different services.

The primary goal of this working group is to develop mechanisms that allow
configuring and concurrently running multiple proxied stream- and datagram-based
flows inside a HTTP connection. The group will specify HTTP and/or HTTP/3
extensions to enable this functionality. The group will focus on a limited set
of client-initiated services: (1) UDP CONNECT and (2) IP proxying.

The working group will also consider fallback to versions of HTTP that operate
over TCP, as resilience to blocking of UDP or HTTP/3 is desired.

Server-initiated services are out of scope.

Multicast UDP and multicast IP support is out of scope. However, the group may
specify extension points that would enable future work on multicast. Specifying
proxy server discovery mechanisms is also out of scope, but the group may
specify techniques for identifying proxy servers to aid future discovery
mechanisms.

The working group will consider the implications of tunneling protocols with
congestion control and loss recovery over MASQUE, and may issue recommendations
accordingly. New congestion control and loss recovery algorithms are out of
scope.

Impacts on address migration, NAT rebinding, and future multipath mechanisms of
QUIC are not anticipated. However, the working group should document these
impacts if they arise.

The group will coordinate closely with other working groups responsible for
maintaining relevant protocol extensions, such as HTTPBIS, QUIC, or TLS. It will
also coordinate closely with ICCRG and TSVWG on congestion control and loss
recovery considerations.
