#### Other Notes to Add into Pi Documentation at Later Date

##### milspecX - 04222020

1. Turn off WIFI management

   - check with 

     ```console
     stark@pi:/ $ iwconfig
     ```

     if Power Management : on, then

     ```console
     stark@pi:/ $ sudo nano /etc/rc.local
     ```

     Before `exit 0` , insert the following

     ```console
     /sbin/iwconfig wlan0 power off
     ```

     Save and exit, `sudo reboot` and recheck `iwconfig`.

2. Change Locale to US.UTF-8

   - Pi Boots up as with GB_. Change this,

     ```console
     sudo nano /etc/locale.gen
     ```

     Remove the # from every line you wish to generate. Save and exit.

     ```console
     stark@pi:/ $ sudo locale-gen
     ```

     Generates the new locale. And check again

     ```console
     locale -a
     ```

     and you should see your new locale. In my case, en_US.utf8.

3. Check and Sync Time with Server

   - Either use Timedatectl or NTP (classic Linux)

   - Check the status

     ```console
     stark@pi:/ $ timedatectl status
     ```

     Is the time zone and local time correct? If not, set with

     ```console
     stark@pi:/ $ timedatectl list-timezones | grep America
     ```

     or as for me, do

     ```console
     stark@pi:/ $ sudo timedatectl set-timezone America/Toronto
     ```

     and check again with status to check that its been changed.

   - NTP-Method.

     ```console
     stark@pi:/ $ sudo apt install ntp
     ```

     Configuration file is here `/etc/ntpd.conf`.

     

     

   

   

   











