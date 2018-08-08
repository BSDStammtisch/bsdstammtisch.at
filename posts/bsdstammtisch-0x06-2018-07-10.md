.. title: BSDStammtisch Wien 0x06 2018-07-10
.. slug: bsdstammtisch-0x06-2018-07-10
.. date: 2018-07-04 16:22:42 UTC+02:00
.. tags: stammtisch, show and tell
.. category: stammtisch
.. link: 
.. description: BSDStammtisch 0x06
.. type: text


## Past meeting 🗓
Tuesday, 2018-07-10, 19:00 (CEST)

## Location 🗺
Seminarraum Technische Informatik, [Operngasse 9, 1040 Wien](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C) Public Transport: U1, U2, U4 Karlsplatz, Bus 59A Bärenmühldurchgang, Nightline N60, N62, N66, N71, Tram 2 (within reasonable walking distance) Bicycle parking: [Just around the corner](https://www.openstreetmap.org/node/419270986#map=18/48.19964/16.36698&layers=C)

## Attendance 🎟
Free for all people interested in learning or discussing about all things BSD! You are welcome!


## Topics
- ZFS boot-environments and beadm(8)
- \#oneWeekOneTool collective self-paced learning
- tmux(1), a terminal multiplexer
- Enough rope to shoot yourself in the foot with ZFS compression and freebsd-update(8)
- Spectre and Meltdown mitigations with microcode deployments
- Please present your topic!
- Show and Tell
	- Show us your quick tips and tricks, the tools you use or recently discovered, be it CLI, GUI, web services, that chocolate chip cookie recipe, a book or conference recording, anything goes. No need to prepare anything.
- Chit chat, food and drinks afterwards

## Shownotes
### Reports and News
- What has happened since the last BSDStammtisch?

### Mixed Topics: 
#### ZFS boot-environments and beadm(8)
Install the package [sysutils/beadm](https://www.freshports.org/sysutils/beadm/) to use ZFS boot environments. You can then easily create, list and switch among your boot environments.  
`beadm list` shows you a list of the currently available environments you could boot from. The currently active system you're booted from is marked with `N`. The one you will be using after a reboot is marked `R`.

http://callfortesting.org/bhyve-boot-environments/

- name: freebsd-update | push /root/freebsd-update.sh script

`/root/freebsd-update.sh`  
```shell
#!/bin/sh -e
# ansible managed
/bin/freebsd-version -ku
export PAGER="/bin/cat -bu"
cd /etc
test -d .git || git init .
git add -A
git commit --allow-empty -am `freebsd-version -ku | sort -r |head -1`-update
zfs snapshot -r zroot@`date -u +%Y%m%d-%H%M`:`freebsd-version -ku | sort -r |head -1`-update
beadm create `freebsd-version -ku | sort -r |head -1`-update
/usr/sbin/freebsd-update --not-running-from-cron fetch install || /usr/bin/true
echo OK freebsd-update complete
echo OK List Boot Environments
beadm list
echo now run "pkg update" and confirm that the changes/reinstall/updates
echo are as expected. Once that has completed, sacrifice a goat and reboot.
```


#### \#oneWeekOneTool collective self-paced learning
#### tmux(1), a terminal multiplexer
After one week playing with `tmux` I dared to publish [my tmux config](https://github.com/MacLemon/dotfiles/blob/master/tmux/.tmux.conf)


#### Enough rope to shoot yourself in the foot with ZFS compression and freebsd-update(8)
Don't try to set your `zroot` ZFS pool to gzip-9 compression and the try to trick your `freebsd-update` to update a `11.1-STABLE` to `11.1-RELEASE`. BSD Loader will fail to load the kernel from the gzip-9 compress zpool.


- Spectre and Meltdown mitigations with microcode deployments


### Show and Tell
- \#oneWeekOneTool - An effort to encourage self-paced learning of the tools, applications and services you use a lot.
- IPMI, Lights out Management, Out of band management
    - Supermicro iKVM, has severe problems with keyboard input, independent of your keyboard locale, even with the on-screen HTML keyboard. You may help yourself to enter a - by using the number-block, or starting any path with `..<tab` to trigger autocompletion.
  - There actually is an [iOS App for SUPERMICRO IPMI](https://itunes.apple.com/at/app/supermicro-ipmiview/id952163566?l=en&mt=8) which works surprisingly good. Typing is uncomfortable, but reliable.
- HP ILO exposes a semi-secret URL which you can use to connect with some VNC clients. `host:port` and `Display` must be set to 2.
- Spectre and Meltdown mitigations, does have a performance hit, turning *off* Hyperthreading may actually improve your performance since there\'s less cache to invalidate
    - port [sysutils/cpupdate](https://www.freshports.org/sysutils/cpupdate/)
  - 
- ZFS snapshot management and replication tools
    - [sysutils/zxfer](https://www.freshports.org/sysutils/zxfer/)
  - [sysutils/znapzend](https://www.freshports.org/sysutils/znapzend/)

Short introductions to tools you like, or that solve a problem for you. This can be anything from GUI, CLI to Webservices, a book, a podcast or conference recording you'd like to recommend or a recipe for chocolate chip cookies. Mmmhhmmmm Cookies! 🍪 No need phor a phanphy prphentaishn.  

## Drinks and Food afterwards
Chit chat and drinks at Fachschaft Informatik fterwards.
