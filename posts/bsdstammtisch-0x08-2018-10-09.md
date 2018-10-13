.. title: BSDStammtisch Wien 0x08 2018-10-09
.. slug: bsdstammtisch-0x08- 2018-10-09
.. date: 2018-09-04 16:22:42 UTC+02:00
.. tags: stammtisch, show and tell
.. category: stammtisch
.. link: 
.. description: BSDStammtisch 0x08
.. type: text


## Past meeting 🗓
Tuesday, 2018-10-09, 19:00 (CEST)

## Location 🗺
Seminarraum Technische Informatik, [Operngasse 9, 1040 Wien](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C) Public Transport: U1, U2, U4 Karlsplatz, Bus 59A Bärenmühldurchgang, Nightline N60, N62, N66, N71, Tram 2 (within reasonable walking distance) Bicycle parking: [Just around the corner](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C)

## Attendance 🎟
Free for all people interested in learning or discussing about all things BSD! You are welcome!


## Topics
- DNS
- DNS hosters
- Problems with modern DNS resource records


## Shownotes 📝

### Reports and News
- What has happened since the last BSDStammtisch?
    - BSDStammtisch.at now [supports TLS 1.3](https://www.ssllabs.com/ssltest/analyze.html?d=bsdstammtisch.at) in the RFC 8446 specification.

Sascha:
#### Lost in Name Resolution
Desire for a little more independence.
Already running your own web- and mail servers, why not run your own resolver?

Observation:
People know DNS, but they don't run their own DNS infrastructure.

Want to run your own Webserver?
There's a million tutorials and a few even have moderately sane defaults.

Easy beginnings:
Run a public resolver! (Uhm, maybe better not!)



##### Unbound
[dns/unbound](https://www.freshports.org/dns/unbound/)
because, why not
usually works fairly well
usually sane by default
Supports DNS-over-TLS
It's made for that, except when it's not.

As usual, running unbound in a FreeBSD/HardenedBSD jail.
Sane for services that are reachable from the internet.

Set sane defaults:
Do not allow to query Adresses in your internal jail range.
Port 853/udp+tcp is used for DNS-over-TLS. (Port not known by `/etc/services` in FreeBSD 11.2.)

Anchor file, contains DNSSec root public key files, so unbound can verify DNSSec answers.

On small DNS instances, with only a few users you'll already get 20-30% cache hits. The more users you have, the better that cache rate gets.


Using DNS-over-TLS is a mixed bag.
Nobody expects DNS queries or any udp traffic on port 853. It's blocked on many networks, especially Cafés and hotels, even by many ISPs.

Many networks even don't allow or expect TCP traffic on port 53, even though that is mandatory by RFC and even absolutely necessary for some query types.
Even fewer allow port 853.

TCP connections are often limited per timeframe. (For exampe UPC WiFree sends you RSTs when you exceed their limit.)

TCP queries requires you to use a forwarder because your system stub resolver can't speak TCP.

unbound is completely retarded as a forwarder and opens a new tcp connection for every query in the resolving process. (#WTFMoments)


- We still need a UDP resolver as fallback.
- We need smarter intermediates that handle failover for upstream DNS servers more geacefully and sane.


##### Traffic amplification attacks:
DNS amplification attacks are the only ones that DNSSec aware EDNS0 queries you'll see on udp. DNSSec signed queries are larger after all.

That's not the fault of DNS.
Some ISPs allow udp packets with faked source addresses.

Not unique to DNS.
Turning off UDP is not really an option.
Smart rate-limiting of DNS queries would be great.
unbound is *not* smart

Possible solution:
- [DNSdist](https://dnsdist.org/) is available in FreeBSD ports: [dns/dnsdist/](https://www.freshports.org/dns/dnsdist/)


Open Questions:
how to properly handle certificate verification fr DNS-over-TLS in an on-demand manner?
Which resolver actually does any of this?

How to get ISPs, and public WiFi to support DNS-over-TLS in their local caching resolvers and allow port 853 queries?

what about bttorrent?
https://freedom-to-tinker.com/2016/09/29/the-effect-of-dns-on-tors-anonymity/

Optimal DNS Slave server: [dns/nsd](https://www.freshports.org/dns/nsd/)


##### A brief overview of DNSSEC:

Signing zones in DNSSEC requires a KSK (Key-Signing-Key), which should be held offline as well as a ZSK (Zone-Signing-Key), which is used to sign your zone. The public key parts of both Keys are present in the DNSKEY records of a signed zone.
Both of these keys can be generated with the help of the ldns-utils package, which also provides commands for zone signing. So it's easy to sign your zone.
*But*: Many DNS providers don't support DS (Delegation signer) records, which need to be present in the (signed) parent zone and contain a hash of the public KSK part.

unbound ]guide for DNS and DNS-over TLS](https://calomel.org/unbound_dns.html) with config samples

