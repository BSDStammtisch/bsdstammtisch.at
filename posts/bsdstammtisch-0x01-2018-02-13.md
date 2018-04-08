.. title: BSDStammtisch Wien 0x01 2018-02-13
.. slug: bsdstammtisch-0x01-2018-02-13
.. date: 2018-02-02 17:18:30 UTC+01:00
.. tags: stammtisch, TU-Wien, Ansible, iocage, jails, show and tell
.. category: stammtisch
.. link: 
.. description: BSDStammtisch 0x01
.. type: text

## Past meeting 🗓
Tuesday, 2018-02-13, 19:00 (CET)

## Location 🗺
Seminarraum Technische Informatik, [Operngasse 9, 1040 Wien](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C)  
Public Transport: U1, U2, U4 Karlsplatz, Bus 59A Bärenmühldurchgang, Nightline N60, N62, N66, N71, Tram 2 (within reasonable walking distance)
Bicycle parking: [Just around the corner](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C)  

## Attendance 🎟
Free for all people interested in learning or discussing about all things BSD! You are welcome!

## Topics 
- Automation with Ansible
- Show and Tell
	- Show us your quick tips and tricks, the tools you use or recently discovered, be it CLI, GUI or web services
- Chit chat and drinks afterwards

## Shownotes 📝
Taken by all the awesome people who attended BSDStammtisch.

## Agenda
- Reports
	- What has happened since the last Stammtisch? (MacLemon)
  - We have [something like a website](/).
  	- The old wien. and graz. hostnames are automatically redirected to the main site
  - We have a [Twitter](https://twitter.com/) account: [@bsdstammtisch](https://twitter.com/bsdstammtisch)
  - We have a [Mastodon](https://mastodon.social/about) account on a BSD focused instance. [@BSDStammtisch@bsd.network](https://bsd.network/@bsdstammtisch) (Mastodon is opensource, federated, awesome and friendly better Twitter)

## Main Talk
- Ansible for freeBSD (Luto)
  - we failed hard: https://github.com/criecm/ansible-iocage because the iocage Plugin for Ansible is in need of some attention.
  - Luto is the ansible guy, MacLemon the BSD guy, so they combined their efforts to get stuff (almost) working
  - Time ran away from Luto, so he shows us ansible basics

### Ansible basics:
- Get [Ansible Information](https://www.ansible.com/ "Ansible is simple IT automation")
- Read [Ansible Documentation](https://docs.ansible.com/ "Ansible Documentation")
- Read [Ansible on BSD](http://docs.ansible.com/ansible/latest/intro_bsd.html)
- To install Ansible on your FreeBSD controller system you can use the port [sysutils/ansible](https://www.freshports.org/sysutils/ansible/ "ansible Radically simple IT automation")
First install Ansible on the machine that pushes the update, the machine to be installed doesn't need anything. Create a file called "inventory" in the directory you want to configure the ansible connection (which basically opens a ssh connection and does awesome stuff with that). 

Controller machine needs python (preferably 2, 3 should be also supported by now)
Controlled machine also needs some kind of python (versions don't need to match)

FreeBSD has no python installed by default, so you need to install this yourself on the controlled machine and tell ansible where to find it there (as ansible comes from the Linux world and BSD puts python in another place).

Ansible configuration files are written in [YAML](https://en.wikipedia.org/wiki/YAML "Wikipedia: YAML Ain't Markup Language")

There is an [Ansible module for ZFS](https://docs.ansible.com/ansible/latest/zfs_module.html "zfs - Manage zfs") which you can use to create datasets, change ZFS properties.

- Show and Tell (Everyone): Briefly show us a practical tool that helps you solve a problem. (Anything goes! Web, CLI, GUI, Services, Literature, Podcasts, Recepies, etc.)
	- [Radicale](https://radicale.org/) CalDAV and CardDAV Server (MacLemon)
  - [NextCloud](https://nextcloud.com) Filesharing, collaboration, Calendar (Jason)
  - [PHO](https://www.purplehat.org/) Mailserver Spam filter solution (Jason)
  - [CryptPad](https://cryptpad.fr) Collaborative Text Editing, Presentations, TODOs (MacLemon)
  	- [CryptPad Talk at FOSDEM](https://fosdem.org/2018/schedule/event/cryptpad/) (Video Recording)
  - [FOSDEM 2018](https://fosdem.org/2018/)  (Albert)
  	- [Video recordings](https://video.fosdem.org/2018/) There are a LOT
    - [BSD DevRoom](https://fosdem.org/2018/schedule/track/bsd/) 11 BSD specific Talks
    - [Lightning Talks](https://fosdem.org/2018/schedule/track/lightning_talks/) 15 Minutes each, short but sweet
    - [Linuxtage Graz](https://www.linuxtage.at/) Named after Linux, but generally welcoming to all open source projects, especially \*BSD.
    	- [Call for participation](https://www.linuxtage.at/call-for-lectures/) is open until 2018-02-18, talks, workshops, booths
	- [Linuxwochen Wien](https://www.linuxwochen.at/Wien/)
  - [Are all BSDs created equally? ](https://media.ccc.de/v/34c3-8968-are_all_bsds_created_equally) A survey of BSD kernel vulnerabilities
  - BSDNow: A regular show about all things \*BSD - Your place to B SD.
  	- [Youtube Channel](https://www.youtube.com/playlist?list=PLUW3LUwQvegyqk2Iqi-YD7Do-AyD4W0s1)
    - [MP3 Podcast](https://itunes.apple.com/at/podcast/bsd-now-mp3/id701045710?l=en&mt=2)
    - [HD Video Podcast](https://itunes.apple.com/at/podcast/bsd-now-hd/id850665429?l=en&mt=2)
  

## Food and Drinks afterwards:
- We ended up at [Fachschaft Informatik](https://www.fsinf.at/) who serve Mate and Kozel (beer) and ordered Pizza together. Many thanks to Astra for hosting us and organizing a room so we could meet!
