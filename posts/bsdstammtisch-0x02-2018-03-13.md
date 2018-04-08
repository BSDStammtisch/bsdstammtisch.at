.. title: BSDStammtisch Wien 0x02 2018-03-13
.. slug: bsdstammtisch-0x01-2018-03-13
.. date: 2018-02-09 17:18:30 UTC+01:00
.. tags: stammtisch, show and tell
.. category: stammtisch
.. link: 
.. description: BSDStammtisch 0x02
.. type: text


## Past meeting 🗓
Tuesday, 2018-03-13, 19:00 (CET)


## Location 🗺
Seminarraum Technische Informatik, [Operngasse 9, 1040 Wien](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C)  
Public Transport: U1, U2, U4 Karlsplatz, Bus 59A Bärenmühldurchgang, Nightline N60, N62, N66, N71, Tram 2 (within reasonable walking distance)  
Bicycle parking: [Just around the corner](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C)  


## Attendance 🎟
Free for all people interested in learning or discussing about all things BSD! You are welcome!


## Topics 
- FreeBSD Jails, `jails.conf` and jail networking
- Please present your topic!
- Show and Tell
	- Show us your quick tips and tricks, the tools you use or recently discovered, be it CLI, GUI, web services, that chocolate chip cookie recipe, a book or conference recording, anything goes. No need to prepare anything.
- Chit chat, food and drinks afterwards


## Shownotes 📝

## Agenda
### Reports
- What has happened since the last BSDStammtisch?
	- We can haz new Logo, already in use on [Twitter](https://twitter.com/BSDStammtisch) and [Mastodon](https://bsd.network/@BSDStammtisch)
	- MacLemon didn't manage to get the website styled in time, sorry for that. It's on the plan for our April meeting.
  - We now have a standard `.ics` calendar you can subscribe to, so you never miss a meeting! [Calendar subscription for BSDStammtisch Wien](https://bsdstammtisch.at/calendar/wien) There are no alerts or reminders in that calendar, we respect the privilege granted by being in your calendar.

### Main Topic: Jails, `jails.conf` and jails networking
Thanks to karu and dch for the huge influx of jail related info in their talks!
Thanks to everbody for sharing big and small tips for *Show and Tell*!

Slides will be made available!

FreeBSD [Jails in the Handbook](https://www.freebsd.org/doc/handbook/jails.html)

#### Jails related commands and files
- [jail(8)](https://www.freebsd.org/cgi/man.cgi?query=jail&apropos=0&sektion=8&manpath=FreeBSD+11.1-RELEASE+and+Ports&arch=default&format=html) --- manage system jails
- [jail.conf(5)](https://www.freebsd.org/cgi/man.cgi?query=jail.conf&sektion=5&apropos=0&manpath=FreeBSD+11.1-RELEASE+and+Ports) --- configuration	file for jail(8)
- [jls(8)](https://www.freebsd.org/cgi/man.cgi?query=jls&sektion=8&apropos=0&manpath=FreeBSD+11.1-RELEASE+and+Ports) --- list jails
- [jexec(8)](https://www.freebsd.org/cgi/man.cgi?query=jexec&sektion=8&apropos=0&manpath=FreeBSD+11.1-RELEASE+and+Ports) --- execute a	command	inside an existing jail

Focusing on the Jails and networking part that is covered with the base system.

A brief history of Jails:

jails are just `chroot` on steroids. As they are basically an extension of the chroot function they feel a bit weird at times today.

jails are used as system containers today despite their original use case as single app containers.
jails normally should have the `securelevel=3` (strongest), except you have a good reason to choose another level.
The not-so-sane default is `securelevel=-1`.

Info on how [FreeBSD handles Securelevels](https://www.freebsd.org/doc/faq/security.html#idp60330472)

#### Jail integration for userland tools
Many command line tools are integrated and know about jails.
- [top(1)](https://www.freebsd.org/cgi/man.cgi?query=top&apropos=0&sektion=0&manpath=FreeBSD+11.1-RELEASE+and+Ports&arch=default&format=html)
- [htop(1)](https://www.freebsd.org/cgi/man.cgi?query=htop&sektion=0&apropos=0&manpath=FreeBSD+11.1-RELEASE+and+Ports)
- [zfs(8)](https://www.freebsd.org/cgi/man.cgi?query=zfs&apropos=0&sektion=0&manpath=FreeBSD+11.1-RELEASE+and+Ports&arch=default&format=html)
- [ps(1)](https://www.freebsd.org/cgi/man.cgi?query=ps&apropos=0&sektion=0&manpath=FreeBSD+11.1-RELEASE+and+Ports&arch=default&format=html)
- [pkg(8)](https://www.freebsd.org/cgi/man.cgi?query=pkg&apropos=0&sektion=0&manpath=FreeBSD+11.1-RELEASE+and+Ports&arch=default&format=html)

#### Security considerations for networking
A jail picks its *first* IPv4|IPv6 address to map the loopback IP `127.0.0.1` (or more specifially `127/8`) and `::1/128`. So the sane way to assign IPs to jails is to first assign a loopback IP on a cloned interface like `lo1` and as a secondary IP you assign the public or local (HOST-side-IPv4-LAN) address and IPv6 addresses.
That way you make sure to not expose any daemons that bind their management interface to the loopback believing that this interface is not exposed to the public internet.

If you do not `set skip on lo1` you can finely control which jail is allowed to talk to which other jail and on which ports.

### Managing Jails with zjail(8)
Even easier than ezjail, zjail lays bare the very fabric of FreeBSD jails.  
[DIY-Jails](https://gitlab.com/skunkwerks/diy-jails/) by dch.



### Show and Tell
Short introductions to tools you like, or that solve a problem for you. This can be anything from GUI, CLI to Webservices, a book, a podcast or conference recording you'd like to recommend or a recipe for chocolate chip cookies. Mmmhhmmmm Cookies! 🍪 No need phor a phanphy prphentaishn.  

#### Security Testing of Websites:
- Firefox extension for playing with Content-Security-Policy
	- [Labratory](https://github.com/april/laboratory)
	- [CSP Tester](https://oxdef.info/csp-tester/)
- Chromium|Chrome Extensions for playing with Content-Security-Policy
	- [CSP Tester](https://chrome.google.com/webstore/detail/csp-tester/ehmipebdmhlmikaopdfoinmcjhhfadlf?hl=en-US)
	- [CSP Evaluator](https://chrome.google.com/webstore/detail/csp-evaluator/fjohamlofnakbnbfjkohkbdigoodcejf?hl=en-US)
- SSLLabs to test the HTTPS of your site and find bugs. For example the [BSDStammtisch.at site](https://www.ssllabs.com/ssltest/analyze.html?d=bsdstammtisch.at)
- Check HTTP Security Headers to instruct browsers to activate certain security features. [BSDStammtisch Security Headers](https://securityheaders.io/?q=bsdstammtisch.at&followRedirects=on)
- Generate a good Content Security Policy for your site with the [CSP Generator](https://report-uri.com/home/generate)
	- The browser console is your friend to find compatibility problems with different browsers since the do not support all the fancy stuff each.
- Maintain Wordpress installations from the command line with [WP-CLI](http://wp-cli.org/) (not available in ports, but reasonable to install and maintain.)
- To test your Wordpress site for known vulnerabilities you can use [WPScan](https://wpscan.org/) which is built in Ruby.

#### Security Testing of XMPP/Jabber Servers (S2S, C2S)
- Security testing your XMPP/Jabber server with the [IM Observatory](https://xmpp.net/) or with [the same tool hosted by process one](https://check.messaging.one/) known for [eJabberd](https://www.freshports.org/net-im/ejabberd/)

#### CLI tools
- Testing DNS still (also from within a jail) with [drill(1)](https://www.freebsd.org/cgi/man.cgi?query=drill&sektion=0&apropos=0&manpath=FreeBSD+11.1-RELEASE+and+Ports) also available in [MacPorts](https://macports.org/) as [drill](https://www.macports.org/ports.php?by=name&substr=drill)

#### Video recommendations
- [CERT.at Video on Meltdown and Spectre](https://www.cert.at/static/downloads/videos/2018-01-10-cert-meltdown-spectre.mp4) (Direct Link to the MP4 video.)

#### ZFS
- ZFS Delegation, see the `jailed` property of ZFS datasets on FreeBSD
- Boot environments, manage them with [sysutils/beadm](https://www.freshports.org/sysutils/beadm/)
- [net/zerotier](https://www.freshports.org/net/zerotier/) - [Network virtualization everywhere](https://zerotier.com/)

#### Jail security
- [chw00t](https://github.com/earthquake/chw00t) - Unices chroot breaking tool
	- [Chw00t: Breaking Unices’ Chroot Solutions](https://www.youtube.com/watch?v=1A7yJxh-fyc) Balazs Bucsay
	- [Slides](https://deepsec.net/docs/Slides/2015/Chw00t_How_To_Break%20Out_from_Various_Chroot_Solutions_-_Bucsay_Balazs.pdf) from [DeepSec](https://deepsec.net) Conference.

## Upcoming events (in chronological order)
- [Linuxtage Graz](https://www.linuxtage.at/) - 2018-04-27..28 (CfP closed)
- [Linuxwochen Wien](https://www.linuxwochen.at/Wien/) - 2018-05-03..05 (CfP open until 2018-05-19)

## Past events
- [AsiaBSDCon](https://asiabsdcon.org/) Videos should be available soon-ish.

## Drinks and Food afterwards
Thanks to [Fachschaft Informatik](https://www.fsinf.at/) for hosting us and providing cold beverages. Thanks for supporting the BSDStammtisch in Wien!
