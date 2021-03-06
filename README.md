mpd-notification
================

**Notify about tracks played by mpd**

This runs in background and produces notifications whenever mpd produces
an event, that is new track is played or playback is paused or stopped.
Notifications look like this:

![Notification](screenshot-sound.png)

This now even supports album artwork:

![Notification with Artwork](screenshot-artwork.png)

Read below for the details.

Requirements
------------

To compile and run `mpd-notification` you need:

* [libav](https://libav.org/) or [ffmpeg](https://www.ffmpeg.org/)
* [libnotify](http://library.gnome.org/devel/notification-spec/)
* [libmpdclient](http://www.musicpd.org/libs/libmpdclient/)
* [markdown](http://daringfireball.net/projects/markdown/) (HTML documentation)
* `gnome-icon-theme` (or anything else that includes an icon named `sound`)

To use `mpd-notification` you probably want `mpd`, the
[music player daemon](http://www.musicpd.org/) itself. ;)

Some systems may require additional development packages for the libraries.
Look for `libnotify-devel`, `libmpdclient-devel` or similar.

Build and install
-----------------

Building and installing is very easy. Just run:

> make

followed by:

> make install

This will place an executable at `/usr/bin/mpd-notification`,
documentation can be found in `/usr/share/doc/mpd-notification/`.
Additionally a desktop file is installed to `/etc/xdg/autostart/`, this
automatically starts the program when logged in to a desktop environment.

Usage
-----

Just run `mpd-notification` after installation or re-login to desktop
environment for autostart.

`mpd-notification` accepts some arguments:

* *-h*: show help
* *-H HOST*: connect to HOST
* *-m MUSIC-DIR*: use MUSIC-DIR for artwork lookup
* *-p PORT*: connect to PORT
* *-v*: verbose output

Artwork
-------

`mpd` does not provide any information where it finds its music files. To make
`mpd-notification` display album artwork you need to tell it where to look for
artwork. You can do that by exporting `XDG_MUSIC_DIR` to your environment or by
specifying `-m` or `--music-dir` on the command line. `mpd-notification` reads
album artwork from `mp3` files, otherwise an image file containing the artwork
needs to be placed in the same directory as the media file and named
`cover.jpg`, `cover.png`, `folder.jpg` or `folder.png`.
