# MASQUE BoF material for IETF 107 

## Agenda

- Agenda bashing, introduction, meeting format (5 mins)
- Problem statement, use cases, and core protocol (30 mins)
  - Overview & use cases
  - Security model
  - Negotiation
  *** there are two core protocol proposals -- we need only one!
- Extensions (30 mins)
  - Proxying
  - Obfuscation
- Charter text discussion (40 mins)
  - Is the core protocol scoped correctly? Does it prohibit or refrain arbitrary extensions?
  - Are there known or blocking dependencies?
  - What is the state of implementations or analysis?
- BoF questions (15 minutes)
  - How many people are interested in seeing this move forward?
  - Set of documents: Core protocol, use cases, extension(s)
  
## Proposed Charter

Many network topologies lead to situations where transport protocol proxying is
beneficial. For example, proxying enables endpoints to communicate when
end-to-end connectivity is not possible and can apply additional encryption
where desirable (such as a VPN).

QUIC is a good candidate protocol for tunneling these types of traffic, as QUIC
provides secure connectivity, multiplexed streams, and connection migration.
Further, HTTP/3 supports an established request/response semantic that can be
used to set up and configure services.

Using QUIC as a tunneling technology allows for proxying of both reliable stream
(TCP) and unreliable datagram (UDP) flows. For stream flows, QUIC streams
provide reliable in-order delivery across the client-proxy link. QUIC datagrams
provide for unreliable data transmission, which allows for transporting UDP and
other unreliable flows via a proxy without introducing potentially redundant or
unnecessary recovery mechanisms. In addition, QUIC can carry both types of flows
over the same connection while taking advantage of a unified congestion
controller.

This working group will work on MASQUE (Multiplexed Application Substrate over
QUIC Encryption), a framework that allows concurrently running multiple proxied
flows inside a QUIC connection. The MASQUE framework will specify a signaling
protocol that is used between the endpoint(s) and the MASQUE server to negotiate
proxy services that establish tunneled connectivity. The initial functionality
will be limited to client-initiated proxy tunnels. The WG may subsequently
recharter to consider other applications.

Proxy services that extend the signaling of the base MASQUE protocol can be
adopted by the group by creating a new milestone with AD review.

If MASQUE requires any extensions to existing protocols, the group will
coordinate closely with the respective group responsible for maintaining that
protocol, such as the HTTPBIS, QUIC, or TLS working groups.
    
## Questions to Answer

https://tools.ietf.org/html/rfc5434

- Is there is a problem that needs solving, and the IETF is the right
group to attempt solving it?

- Is there is a critical mass of participants willing to work on the
problem (e.g., write drafts, review drafts, etc.)?

- Is the scope of the problem is well defined and understood, that
is, people generally understand what the WG will work on (and
what it won't) and what its actual deliverables will be?

- Is there is agreement that the specific deliverables (i.e.,
proposed documents) are the right set?

- It is believed that the WG has a reasonable probability of
having success (i.e., in completing the deliverables in its
charter in a timely fashion)?

## Questions/Issues Raised

- Does this change the QUIC security model? (Removing one layer of encryption when there's three parties involved?)
  - There's much confusion about layering and tunnel encryption. Let's draw some diagrams to clarify?
- Enterprise proxy and client trust issue(s)?

## References:
- https://datatracker.ietf.org/doc/draft-schinazi-masque/
- https://datatracker.ietf.org/doc/draft-schinazi-masque-obfuscation/
- https://datatracker.ietf.org/doc/draft-kuehlewind-quic-substrate/
- https://datatracker.ietf.org/doc/draft-piraux-quic-tunnel/
- https://datatracker.ietf.org/doc/draft-kuehlewind-quic-proxy-discovery/
