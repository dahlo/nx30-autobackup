nx30-autobackup
=================

When this set of scripts is configured correctly, the
Samsung NX30 will automatically backup all photos and
videos via scp whenever the camera is turned on.

Based on https://github.com/jdieter/nx300m-autobackup and modified to work with the NX30.

##Installing##
Tested on version XXXX of the firmware. It may or may not work on other versions.

Copy the contents of the sdcard directory onto the sdcard
from the camera.

In autobackup/config:

1. Set the ESSID of the network you want to connect to
2. Set the hostname you want to connect to in the form
user@hostname
3. Set the path you want to copy the files to on the
destination

Then:
Copy the id_rsa and id_rsa.pub to autobackup/ssh for a
user with write permissions to the destination

##Details##
autoexec.sh is run every time the camera is turned on and
calls autobackup/backup.sh.

backup.sh checks to see if there are any new files that
haven't been backed up yet, and, if there are, connects to
the listed WiFi AP, runs a "keep alive" script so the
camera won't automatically shut down, and sends each new
file to the backup server.  After all the new files have
been sent, it shuts down the WiFi connection and the "keep
alive" script.

## TODO
1. Get it to work.
