# Installing Raspberry Pi - Headless Method

Quick summary of steps that I found useful in reinstalling a fresh raspian image onto an existing Raspian uSD card.

Quite often, I've found myself reinstalling the Raspian image to a uSD card that's been already preloaded with a previous Raspian build. Working in a MacOS environment, the filesystems are therefore incompatible (RPi used ext4) and therefore, will not mount easily.

Combing through Google's search returns, there's a nifty page by [Jeff Geerling](https://www.jeffgeerling.com/blog/2017/mount-raspberry-pi-sd-card-on-mac-read-only-osxfuse-and-ext4fuse) that answered my torment: where he's found an open source tool that mounts the ext4 filesystem onto the Mac.  

Here's the instructions:

```console
stark@raspberrypi:/$ brew cask install osxfuse
```

```console
stark@raspberrypi:/$ brew install ext4fuse
```

```console
stark@raspberrypi:/$ diskutil list
```

You should then see an output list of the mounted drives. Look for your drive.

