#  Installing Raspberry Pi - Headless Method

Quick summary of steps that I found useful in reinstalling a fresh raspian image onto an existing Raspian uSD card.

Quite often, I've found myself reinstalling the Raspian image to a uSD card that's been already preloaded with a previous Raspian build. Working in a MacOS environment, the filesystems are therefore incompatible (RPi used ext4) and therefore, will not mount easily.

Combing through Google's search returns, there's a nifty page by [Jeff Geerling](https://www.jeffgeerling.com/blog/2017/mount-raspberry-pi-sd-card-on-mac-read-only-osxfuse-and-ext4fuse) that answered my torment: where he's found an open source tool that mounts the ext4 filesystem onto the Mac.  

Here's the instructions:

```console
stark@:/$ brew cask install osxfuse
```

```console
stark@:/$ brew install ext4fuse
```

```console
stark@:/$ diskutil list
```

You should then see an output list of the mounted drives. Look for your drive. Then create a mount point:

```console
stark@:/$ sudo mkdir /Volumes/rpi
```

Mount the drive using ext4fuse:

```console
stark@:/$ sudo ext4fuse /dev/disk2s2 /Volumes/rpi -o allow_other
```

Then do your thing and format the uSD card and install using Pi imaging software from the foundation.

After installing the Pi image, navigate into the card at boot directory. Do the following:

```console
$ touch wpa_supplicant.conf
$ sudo nano wpa_supplicant.conf
```

Then enter the following:

```console
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=<Insert 2 letter ISO 3166-1 country code here>

network={
  ssid="<Name of your WIFI>"
  psk="<Password for your WIFI>"
}
```

Save it and exit back to command line. Then do the following in the same boot folder:

```console
stark@:/$ touch ssh
```

No extension needed. Eject the card. In the event that the card won't eject, do the following [source](http://www.andreaswacker.com/blog/2006/03/16/umount-unmountvolumesyour-disk-name-resource-busy/):

```console
stark@:/$ umount -f /your/device/path
```

Plug in the uSD into the Pi and start it. When the Pi boots, it looks for the ssh file and starts...

Where's the Pi? Use:

```console
$ arp -a
```

Look for something: 192.168.x.x or 10.x.x.x. Then,

```console
$ ssh pi@10.x.x.x
```





