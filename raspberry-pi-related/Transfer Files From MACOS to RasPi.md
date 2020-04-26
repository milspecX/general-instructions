##### How To Transfer Files from MacOS to Raspberry Pi

##### milspecX - 04222020

In console,

```console
stark:~$ scp /<directory-where-file-resides>/Test.txt pi@address:
```

Remember the colon at the end of command ':'.

Example:

```console
stark:~$ scp /Users/stark/Desktop/Hello.txt pi@10.0.1.65:
```

What about from Pi to MacOs? Do this:

In MacOs terminal, in the directory where you want to save the file:

```console
stark:~$ scp pi@10.0.1.65:/media/usb/file2mv2MacOs.txt .
```

Note: remember the period after the filename.









