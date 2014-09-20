Overview
========
A simple command line python script that transcodes a list of files from a
few different audio encodings to mp3. Useful when you have FLAC files that
you want to play in iTunes or anything else that doesn't support FLAC.

Files are written to the local directory in a file hierarchy that mirrors
the source file hierarchy.

Currently supports transcoding from FLAC, ogg, and m4a. Any mp3 files in the
list of files will be copied verbatim.

Runs multiple threads for decoding/encoding, to take advantage of computers
with multiple CPUs and/or multiple cores.

Available at https://github.com/markdoliner/transcode_to_mp3


Requirements
============
* python Mutagen library.
  * Homepage: https://bitbucket.org/lazka/mutagen
  * Ubuntu: apt-get install python-mutagen
* python psutil library.
  * Homepage: https://github.com/giampaolo/psutil
  * Ubuntu: apt-get install python-psutil
* Libav (for the avconv command line utility)
  * Homepage: https://libav.org/
  * Ubuntu: apt-get install libav-tools
* LAME MP3 encoder
  * Homepage: http://lame.sourceforge.net/
  * Ubuntu: apt-get install lame


Usage
=====
The script was developed on Linux. It might work on other Unixy operating
systems such as OS X and possibly even Microsoft Windows. Especially if
subprocess.PIPE is supported.

The first argument should be the top level base directory where your music
files live. All subsequent arguments should be files or directories underneath
the top directory.

Example:
<pre>
> mkdir music_for_my_ipod
> cd music_for_my_ipod
> transcode_to_mp3 /mnt/music /mnt/music/Bananarama\ -\ Cruel\ Summer.flac /mnt/music/Hooverphonic/
</pre>

This runs for a bit, copying files and transcoding as necessary, and
eventually results in a directory hierarchy that looks like this:
<pre>
./music_for_my_ipod/Bananarama - Cruel Summer.mp3
./music_for_my_ipod/Hooverphonic/The Magnificent Tree/01 Autoharp.mp3
./music_for_my_ipod/Hooverphonic/The Magnificent Tree/02 Mad About You.mp3
...
./music_for_my_ipod/Hooverphonic/The Magnificent Tree/11 L'odeur Animale.mp3
</pre>
