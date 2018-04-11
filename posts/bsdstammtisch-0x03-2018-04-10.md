.. title: BSDStammtisch Wien 0x03 2018-04-10
.. slug: bsdstammtisch-0x03-2018-03-13
.. date: 2018-03-14 18:31:30 UTC+01:00
.. tags: stammtisch, show and tell
.. category: stammtisch
.. link: 
.. description: BSDStammtisch 0x03
.. type: text


## Past meeting 🗓
Tuesday, 2018-04-10, 19:00 (CEST)


## Location 🗺
Seminarraum Technische Informatik, [Operngasse 9, 1040 Wien](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C) Public Transport: U1, U2, U4 Karlsplatz, Bus 59A Bärenmühldurchgang, Nightline N60, N62, N66, N71, Tram 2 (within reasonable walking distance) Bicycle parking: [Just around the corner](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C)


## Attendance 🎟
Free for all people interested in learning or discussing about all things BSD! You are welcome!


## Topics 
- Backups (occasionally…) - A beta version of a talk, and a discussion on how to keep your data safe and secure.
- Please present your topic!
- Show and Tell
	- Show us your quick tips and tricks, the tools you use or recently discovered, be it CLI, GUI, web services, that chocolate chip cookie recipe, a book or conference recording, anything goes. No need to prepare anything.
- Chit chat, food and drinks afterwards


## Shownotes 📝
### Reports and News
What has happened since the last BSDStammtisch?  


#### We can haz automated Website builds now!
Thanks to [@fredl](https://bsd.network/@fredl) we now have automated testing and deployment builds for our website. The source is pushed to [GitHub](https://github.com/BSDStammtisch/bsdstammtisch.at). To add content or improve the website, or create a more fancy theme, either fork and send a pull request or hand your public SSH (-t ed25519) key to fredl or MacLemon so you can directly push to our webserver.  


#### Stickers anyone?
Yes, people would like stickers. MacLemon will take care of getting them. You're welcome to donate a few € to the cause.


### Main Topic: Backups (occasionally)
A *beta* version of a talk about how to keep your data save and secure or how to verifiably lose it all. Lessons learned the hard way.  
Many bad jokes, old floppies and things to think about when trying to backup data that can actually be restored as well. (Slides will follow after they've been reworked. If they haven't been published by the May meeting, please poke [@MacLemon](https://chaos.social/@MacLemon)!)  

### Show and Tell
Short introductions to tools you like, or that solve a problem for you. This can be anything from GUI, CLI to Webservices, a book, a podcast or conference recording you'd like to recommend or a recipe for chocolate chip cookies. Mmmhhmmmm Cookies! 🍪 No need phor a phanphy prphentaishn.  

#### NAS4Free on QNAP
Adi brought a small NAS/home-server ([QNAP TS251+](https://www.qnap.com/en-us/product/ts-251+)). OS is [NAS4Free](https://www.nas4free.org), which is FreeBSD based.  
Problems I have:  
1. Fan speed control is always at maximum which is very annoying.
2. Server and/or HDDs should hibernate when not in use and only power on when server is accessed.
3. Related to today's topic a backup strategy under ZFS for a 2-bay server is needed. One HDD should be able to rollback file versions for 6 months and sychronize itself once per week with the primary disk - rsync.

#### Mixed backup tools for FreeBSD used by peopl
- [sysutils/restic](https://restic.net/) (incremental, deduplication, local encryption, destination can be SFTP, S3, HTTPS, local disk, etc.)
- [net/rsync](https://rsync.samba.org/) (incremental, hardlinks, destination can be local or remote storage via SSH or rsync protocol.)
- [sysutils/tarsnap](https://www.tarsnap.com/) (commercial, client FOSS, local encryption, destination is hosted cloud storage)
- [sysutils/rsnapshot](http://rsnapshot.org/)
- [archivers/py-borgbackup](https://www.borgbackup.org/)
- [sysutils/bacula](http://blog.bacula.org/)
- [sysutils/duplicity](http://duplicity.nongnu.org/)
- [sysutils/life-preserver](https://www.trueos.org/handbook/advanced.html#restore-from-life-preserver-backup) (Part of [TrueOS](https://trueos.org/), also in ports)
- [sysutils/znapzend](http://www.znapzend.org/) (ZFS snapshot and replication manager around ZFS send, Perl)
- [sysutils/zrepl](https://zrepl.github.io/) (ZFS Snapshot and replication manager)

Did we miss any tool you like or would recommend? Please [add it to the list](https://github.com/BSDStammtisch/bsdstammtisch.at) and talk about it at one of our next meetings in Show and Tell or give a full fledged presentation if you like! Thanks for contributing!

#### Other things we talked about
- [FreeNAS](https://www.freenas.org/)

## Drinks and Food afterwards
Thanks to [Fachschaft Informatik](https://www.fsinf.at/) for hosting us and providing cold beverages. Thanks for supporting the BSDStammtisch in Wien!
