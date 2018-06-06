.. title: BSDStammtisch Wien 0x04 2018-05-08
.. slug: bsdstammtisch-0x04-2018-05-08
.. date: 2018-04-11 14:22:42 UTC+02:00
.. tags: stammtisch, show and tell
.. category: stammtisch
.. link: 
.. description: BSDStammtisch 0x04
.. type: text


## Past meeting 🗓
Tuesday, 2018-05-08, 19:00 (CEST)


## Location 🗺
Seminarraum Technische Informatik, [Operngasse 9, 1040 Wien](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C) Public Transport: U1, U2, U4          Karlsplatz, Bus 59A Bärenmühldurchgang, Nightline N60, N62, N66, N71, Tram 2 (within reasonable walking distance) Bicycle parking: [Just around the corner](https://www.           openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C)

## Attendance 🎟
Free for all people interested in learning or discussing about all things BSD! You are welcome!

### Main Topic: pf(4) routing domains
- pf(4) and routing domains in OpenBSD


#### OpenBSD, pf and routing
This will apply to OpenBSD `pf(4)`, if you want to do the same on FreeBSD, you'll likely have to chang the syntax somewhat since FreeBSD uses an older version of `pf` which has a different syntax.

`pf` is available on OpenBSD, FreeBSD, macOS, NetBSD. It's the standard packet filter, which controls packets.

Rulesets are always evaluated from top to bottom. The *last* rule that matches that designates the packet's destiny.

OpenBSD by default blocks the `_pbuild` user used to compile ports from accessing the network to ensure that ports always build even when there is no network available. Violations to that rule are always logged.

`scrubbing` means that fragmented packets are reassembled and TTL is enforced. It should be on at all times, though it's not required on endpoints, opposed to firewalls and routers.

Port numbers can be taken as a name as long as it exists in `/etc/services` and protocols as well as long as they exist in `/etc/protocols`.

Unlike other packet filters `pf` ist stateful by default.
`pf` by default doesn't care about the IP version. When restricting a rule with an explicit IPv4 address, pf is smart enough to know that this rule can not apply to IPv6 and vice-versa.

With block or pass only the last rule is used. 
When using a `match` rule, the action is always taken, for example log. A match rule gives a packet a marker, it doesn't yet decide if the packet itself is accepted or rejected by a later rule.

`quick` changes the way how rules are evaluated. When a `quick` rule matches, it's executed immediately and no more rules get evaluated.

Rules may be restricted to ingress (in) or egress (out) traffic.

Ports can be specified as ranges, though the syntax is sometimes a little awkward.

Interfaces are transparently replaced by their current IP address. You can also dynamically reference the :network, :broadcast or :peer (point-to-point).
When using dynamic IPs you can enclose the interface namen in braces like (em0) and the IP of the interface is evaluated at runtime when the rule is evaluated. Otherwise it's IP is replaced when loading he ruleset. This comes in handy with laptops that roam networks.



##### Lists
{tcp, udp}
{http, https}
Lists get expanded to a separate rules for each list item, in that order.

##### Macros
(aka variables)
Macros allow abstraction of physical interfaces to %names. Saves a lot of headache when things change and reduces the risk of typos. Makes rules a lot more readable.


##### Options
skip, skips filtering on an interface (usually used on lo0)
set syncookies always|*never*|adaptive
set optimization (optimizes state timeouts)
set ruleset-optimization (removes rules that never match)

Inspecting the active ruleset
`pfctl -s rules`
Evaluating a ruleset without activating it (syntax checking): `pcftl -f /etc/pf.conf -n`

##### NAT und redirection
nat-to for source nat
rdr-to for incoming nat
binat-to expands to nat-to and rdr-to makes 1:1 mappings.
af-to for translation between different addrss families (NAT64) (only on OpenBSD, not available on FreeBSD)

##### Further topics
- scrubbing
- tables (can change during runtime, like lists of IPs, networks, etc. Daemons can build these, like spamd)
- anchors (apply rulesets under certain conditions)
- logging (pf logs the rule number that caused the logging) 

##### pf, routing and rdomains
failover and load balancing
Two WAN interfaces, one local network.
Either for load balancing traffic or failover when one WAN goes down.

Routes and priorities
failover is realized with routes of different -priority

multipath
Needs to have -mpath option set.

failover typically relies on ifstated to monitor interfaces.

pf *can* do routing, but doesn't really want to.


##### routing domains
Routing domains are similar to networking namepsaces in Linux. A routing domains hat is own routes and interfaces assigned to it.
By default all interfaces share a single routing domain, the default rdomain `r0`.

processes can be put into a rdomain and only see its routes, but not any other available routes.

A routing domain is implicitly created by assigning an interface to it.
You cannot delete rdomains.

This is reflected in the output of `ifconfig`.

network config in `/etc/hostname.<if>` can be made permanent.

```/etc/hostname.em1
rdomain 1
dhcp
…
```

pair(4) devices in different rdomains. They're used to connect rdomains to one another.
pair interfaces get patched to connect them.
ifconfig pair1 patch pair10
ifconfig pair2 patch pair20

It's recommended to always create a loopback adresses inside the rdomains:
ifconfig lo1 127.0.0.1 255.0.0.0 rdomain 1 up
ifconfig lo2 127.0.0.1 255.0.0.0 rdomain 2 up

The loopback interfaces must have separate names, but each loopback does indeed have its own 127.0.0.1 address. (Unlike FreeBSD jails.)

Pair interfaces are quite new (added in OpenBSD 5.9). Before you had to route these with pf, but pf doesn't want to do routing.

rc.d daemon scripts have rtable/rdomain support via the daemon_rtable caribale. This way you can e.g. start `sshd` in various rdomains at startup or have specific daemins in certain rdomains.






### Show and Tell
Short introductions to tools you like, or that solve a problem for you. This can be anything from GUI, CLI to Webservices, a sbook, a podcast or conference recording you'd like to recommend or a recipe for chocolate chip cookies. Mmmhhmmmm Cookies! 🍪 No need phor a phanphy prphentaishn.  

#### Better Crypto - Applied Crypto Hardening
We're working on updates! BSD testing of settings is welcome!
[Better Crypto](https://Bettercrypto.org/)



#### Grazer Linuxtage
Videos are available online [Media CCC](https://media.ccc.de/c/glt18)

#### LibreSSL
LibreSSL portable breaks a bunch of ports.  
- postfix
- mysql 5.7


#### BSD Hardware monitor
https://github.com/koitsu/bsdhwmon
FreeBSD pkg is very outdated. Building from source is easy, just do `make`.
Hardware support is very limited. Basically a bunch of older Supermicro motherboards is supported. (X6-X8, nothing newer.)
None of the hardware I have under my control is supported. Maybe in the future.


## Drinks and Food afterwards
Chit chat, food and drinks afterwards.
