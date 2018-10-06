.. title: BSDStammtisch Wien 0x07 2018-09-11
.. slug: bsdstammtisch-0x07-2018-09-11
.. date: 2018-08-04 16:22:42 UTC+02:00
.. tags: stammtisch, show and tell
.. category: stammtisch
.. link: 
.. description: BSDStammtisch 0x07
.. type: text


## Past meeting 🗓
Tuesday, 2018-09-11, 19:00 (CEST)

## Location 🗺
Seminarraum Technische Informatik, [Operngasse 9, 1040 Wien](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C) Public Transport: U1, U2, U4 Karlsplatz, Bus 59A Bärenmühldurchgang, Nightline N60, N62, N66, N71, Tram 2 (within reasonable walking distance) Bicycle parking: [Just around the corner](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C)

## Attendance 🎟
Free for all people interested in learning or discussing about all things BSD! You are welcome!

## Shownotes
### Reports and News
- What has happened since the last BSDStammtisch?

### Topics
- NAT64/DNS64
- [OpenZFS Developer Summit 2018](http://www.open-zfs.org/wiki/OpenZFS_Developer_Summit_2018) [Re-Live](https://livestream.com/accounts/27705503/events/8358074/player?width=960&height=540&enableInfoAndActivity=true&defaultDrawer=feed&autoPlay=true&mute=false)
- [MRMCD 2018](https://mrmcd.net/) happend
- [EuroBSDcon](https://2018.eurobsdcon.org/) coming up
- [BalcCon](https://2k18.balccon.org/) coming up
- Running SPF:Sender Rewriting Scheme on your MTA?
- Recommended DNS Providers that support CAA, TLSA and DNSSec? Are there any in Austria?
- Hetzner Cloud bietet nun OpenBSD und FreeBSD Installations.ISOs für VMs an.

- DMARC Analyse Tools und Services
  - https://domainaware.github.io/parsedmarc/
  - https://www.dmarcanalyzer.com/
  - https://www.fraudmarc.com/
  - https://dmarcian.com/
  
### Show and Tell 
  
- The [pfSense Book](https://www.netgate.com/docs/pfsense/book/) is now free and OpenSource.

#### NAT64/DNS64
Mixing Jails with RFC1918 addresses and public IPs is kind of painful. Jail source IP selection seems to be broken in FreeBSD, so why not skip the `binat` config for pf(8) for external IPs and skip legacy IP for jails completely? Internal jail communication will be done via IPv6 only.

Damit wird dann 6-to-4 Adressmapping gemacht und das geht mit DNS64.
Existierende IPv6 Adressen funktionieren wie gewohnt, wenn nur ein A record für einen Hostnamen existiert, werden die 32bit der IPv4 Adresse in die letzen 32bit des eigenen IPv6 Prefixes hineingeschrieben.
  
FreeBSD Jails die *nur* noch IPv6 haben, sind durchaus problematisch. Sendmail und unbound starten ohne IPv4 nicht da sie zwar auf loopback binden, aber nur 127.0.0.1, also das IPv4 loopback. Wenn bei beiden Daemons auch ein listen auf ::1 (IPv6 loopback) konfiguriert wird, funktioniert es auch.

NAT64 erlaubt uns dann Routing von gemappten IPv4 über IPv6 zu konfigurieren.
In `ipfw` (leider nicht in pf(8)) kann NAT64 konfiguriert werden.


## Drinks and Food afterwards
Chit chat, food and drinks afterwards.

