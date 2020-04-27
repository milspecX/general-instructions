#### How to Mount USB Flash/Drive to RPi - ExFAT

##### milspecX

##### 04262020

1. If needed, install exFAT first!

   ```console
   sudo apt-get update
   sudo apt-get upgrade
   sudo apt-get install exfat-fuse
   sudo apt-get install exfat-utils
   ```

2. Plug in device to @Pi

3. In console,

   ```console
   stark@:/ $ ls -l /dev/disk/by-uuid
   ```

3. Look for /sda such as `sda1`. Note your ID (aka XXXX-XXXX)

4. Create a mount point somewhere,

   ```console
   stark@:/ $ sudo mkdir /media/usb
   stark@:/ $ sudo chown -R <user>:<user> /media/usb
   ```

5. To manually mount the drive,

   ```console
   stark@:/ $ sudo mount /dev/sda1 /media/usb -o uid=<user>, gid=<user>
   ```

   Or:

   ```console
   sudo mount -t exfat /dev/sda1 /media/usb
   ```

   -o allows you to write as well as read.

6. To unmount,

   ```console
   stark@:/ $ umount /media/usb
   ```

Up till now, its just manual. Let's automount so that the Pi mounts the drive each time it starts up.

```console
stark@:/ $ sudo nano /etc/fstab
```

7. Add this at the end of file,

```console
UUID=XXXX-XXXX /media/usb exfat auto,nofail,noatime,users,rw,uid=<user>,gid=<user> 0 0
```

nofail allows the boot process to proceed even if there's no disk plugged in.

```console
stark@:/ $ sudo reboot
```

Check - drive should now be mounted onto RPi.











