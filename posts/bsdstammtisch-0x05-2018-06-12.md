.. title: BSDStammtisch Wien 0x05 2018-06-12
.. slug: bsdstammtisch-0x05-2018-06-12
.. date: 2018-06-10 16:22:42 UTC+02:00
.. tags: stammtisch, show and tell
.. category: stammtisch
.. link: 
.. description: BSDStammtisch 0x05
.. type: text


## Next meeting 🗓
Tuesday, 2018-06-12, 19:00 (CEST)

## Location 🗺
Seminarraum Technische Informatik, [Operngasse 9, 1040 Wien](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C) Public Transport: U1, U2, U4  Karlsplatz, Bus 59A Bärenmühldurchgang, Nightline N60, N62, N66, N71, Tram 2 (within reasonable walking distance) Bicycle parking: [Just around the                    corner](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C)

## Attendance 🎟
Free for all people interested in learning or discussing about all things BSD! You are welcome!


## Topics 
- Please present your topic!
- pkg(8) and ports best practices, tips and tricks
- how to package software for OpenBSD and FreeBSD
- Show and Tell
	- Show us your quick tips and tricks, the tools you use or recently discovered, be it CLI, GUI, web services, that chocolate chip cookie recipe, a book or conference recording, anything goes. No need to prepare anything.
- Chit chat, food and drinks afterwards

## Shownotes
### Reports and News
- What has happened since the last BSDStammtisch?

### Main Topic: <Title of the upcoming main topic>
- packages, ports, tips and tricks and what to avoid
  
- https://hackmd.io/s/HkwIhv6x7 via dch@
- A [minimal port](https://github.com/iwantmyname/simple) example


- Interesting things to put into your `/etc/make.conf`
    - Autoaccept these licenses: `LICENSES_ACCEPTED+= MIT BSD3CLAUS APACHe20 LGPLV3 BSD2CLAUSE MPL`
    - Never build Kerberos support (for example in [ftp/curl](https://www.freshports.org/ftp/curl/)) `OPTIONS_UNSET = GSSAPI_BASE`

- [EuroBSDCon](https://2018.eurobsdcon.org/) 2018-09-22..23 in Bucureşti – România

### Show and Tell
Short introductions to tools you like, or that solve a problem for you. This can be anything from GUI, CLI to Webservices, a book, a podcast or conference recording you'd like to recommend or a recipe for chocolate chip cookies. Mmmhhmmmm Cookies! 🍪 No need phor a phanphy prphentaishn.  

- [textproc/jq](https://www.freshports.org/textproc/jq/) Lightweight and flexible command-line JSON processor
- [BSDCan 2018](https://www.bsdcan.org/2018/) happend ([Schdule](https://www.bsdcan.org/2018/schedule/day_2018-06-08.en.html))

#### FreeNAS
- Handy utility to identify and mark drives in a chassis. (Like blink the RED LED on them to mark a dead drive to be swapped out for a new one.)
    - For LSI/Avago HBAs or RAID controllers:
    - SAS2 controllers: `/usr/local/bin/sas2ircu`
    - SAS3 controllers: `/usr/local/bin/sas3ircu`


### Books
- A philospohy of software design (John Ousterhout) ISBN13: 9781732102200

## Drinks and Food afterwards
Chit chat, food and drinks afterwards.
