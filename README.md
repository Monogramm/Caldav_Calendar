Elastic Skin Support now available

* First thing to know. If you are updating this plugin from 0.5.x to 0.6.x, a clean install is required. Eead the [Update Info](update_guide.md) page for details.#


I made this as a working, out of the box, calendar for use with Roundcube (Version 1.4.1) and Nextcloud (Version 17 is the latest known working).

I will update this when needed by deprecated purposes or when Nextcloud changes their sabre version.

This is a fork of Kolab and FasterIT calendars combining the best of both and using the sabre from Nextcloud to work with it's version of sabre. It will sync already existing calendars. If you want more than the default, you must add calendar within Nextcloud and then go back to Roundcube and it should be there automatically. From Roundcube, you can add, edit and delete events and will be in sync with Nextcloud.

This is also compatible with RCMCARDDAV 3.0.3 as I use it to sync my contacts with Nextcloud to Roundcube as well.

This was tested using Roundcube 1.4-RC1 and PHP 7.2.11.

For Roundcube 1.3 download ver 0.4 here https://github.com/texxasrulez/Caldav_Calendar/releases/tag/0.4

Latest merge with Kolab 3.5.2

I have kept Kolab libkolab folder with this fork to keep compatible with kolab, just with a better caldav implementation.

_________________________________________________________________________________________

Installation is pretty straight forward. I wouldn't use composer to install, just download repo from github and follow the directions below:

Copy calendar, libcalendaring and libkolab folders to Roundcube Plugin folder, copy config.inc.php.dist to config.inc.php, located in root of calendar directory, and change:
* domain.ltd to your URL. 'These URL's are already configured for the default calendar url for Nextcloud.'
* calendar_crypt_key to any random sequence of characters.
* calendar_itip_smtp_server to the SMTP server of yours or set it empty ''.

 Import sql schemas located in /driver/* folders to your database.	Import the corresponding (MySQL, Postgres) initial SQL schema located in calendar/drivers/*/SQL/ folder to your roundcube database.

Add "calendar" to $config['plugins'] in your Roundcube main config file and you are set.

***IMPORTANT***

Your username and password must be the same for Nextcloud and Roundcube to work properly.

Known Issues:
-------
* ~~Incompatible libcalendaring with Tasklist (WIP to make compatible)~~ Fixed!!!!
* Will not create new calendar from Roundcube GUI.
* ~~Itip does not send reply to event organizer using RC1.3. Works in RC1.2.4.~~ Fixed!!!!
* Recurring events marked as "All Day Events" will be a day early the following years.- Darn bug crept back in. Help is requested
* Database driver does not work. Birthdays are the issue due to being all day.

User Discovered Issues:
-------
* ~~Check Calendar shows Error 500.~~ Fixed!!!!

If anyone would like to help out to make oauth and other features work, I would truly appreciate it.
Otherwise, issues are always welcome but I do ask that you provide as detailed info as you can ie, roundcube logs, system logs, OS info and any other pertinant information that you think can be helpful. I do thank you ...


TODO:
-------
* Ability to add new calendar to Nextcloud from Roundcube Calendar GUI.
* Oauth support. (TBD. My skills aren't the best. :-(  ....  I need some help)
* Assign random colors to autodiscover calendars.
* ~~Remove mcrypt and replace with openssl.~~ Fixed!!!!

Random Color Quickie:
-------
* Multiple Calendars saved with same color. (Import into database `UPDATE caldav_calendars SET color = substring(MD5(RAND()), -6);` to assign radmon colors after initial sync of calendars)

Persistant Log Error:
-------
* [29-Jan-2020 21:02:25 America/Los_Angeles] PHP Warning:  feof() expects parameter 1 to be resource, null given in /path_to_roundcube/plugins/calendar/lib/vendor/sabre/vobject/lib/Parser/MimeDir.php on line 245
* [29-Jan-2020 21:02:25 America/Los_Angeles] PHP Warning:  fgets() expects parameter 1 to be resource, null given in /path_to_roundcube/plugins/calendar/lib/vendor/sabre/vobject/lib/Parser/MimeDir.php on line 247
* [29-Jan-2020 21:02:25 America/Los_Angeles] PHP Warning:  feof() expects parameter 1 to be resource, null given in /path_to_roundcube/plugins/calendar/lib/vendor/sabre/vobject/lib/Parser/MimeDir.php on line 249
* [29-Jan-2020 21:02:25 -0800]: <179594f3> PHP Error: iCal data parse error: Error reading from input stream in /path_to_roundcube/plugins/libcalendaring on line 163 (POST /mail/?_task=calendar&_action=refresh)
