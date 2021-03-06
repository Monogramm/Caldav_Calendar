# Texas Edition Caldav Calendar Plugin for Roundcube & NextCloud

## WARNING - This Repo is not for the faint of heart
Be warned. This is **NOT** intended for Production Use. \
This plugin will be under constant development for the foreseeable future with **ASOLUTELY NO SUPPORT** at the moment. As soon as I get the new features added and operating as expected, support will **MOST DEFINATELY** resume. \
Never fret, I have a Stable Version Ready to Rock 'n Roll. Download below ...  \
[Stable Version](https://github.com/texxasrulez/caldav_calendar) - LTS Version.

**USE AT YOUR OWN RISK**

**Tested and working using the following:**
* Roundcube v1.4.7
* Composer v1.10.9
* Nextcloud v18.0
* PHP v7.2.32
* MySQL Server v5.7.31

**Elastic Skin Support now available**

I forked this with the intent to make a working, out of the box caldav enabled calendar for exclusive use with Nextcloud.

I will maintain this repo for as long as I can.

This plugin is intended to be used with Nexcloud only at this point in time. The Calendar Plugin will sync already existing calendars from Nextcloud. If you want more than the default, you must add calendar within Nextcloud Calendar GUI and then go back to Roundcube and it will magically appear in your Roundcube Calendar GUI after a good refresh (F5). From Roundcube Calendar GUI, you can add, edit, delete, download, copy and add attachments to events. iTip invitations are succesfully sent, accepted, declined, etc upon inviting attendees ... 

This is verified as compatible with RCMCARDDAV 3.0.3 as I use it to sync my contacts from Nextcloud to Roundcube.

For Older Roundcube versions (v1.3.x and older) download [v0.4](https://github.com/texxasrulez/caldav_calendar_te/releases/tag/0.4)


**Installation** [Detailed Instructions](https://github.com/texxasrulez/caldav_calendar_te/blob/master/detailed_install_instructions.md)

1. Download zip file of the latest release or most current commit in master branch from github
1. Copy/FTP/Upload calendar, libcalendaring and libkolab folders to Roundcube Plugin folder. 
1. Run `composer install` in calendar plugin directory. If not installed globally run `php composer.phar install`  
2. Copy config.inc.php.dist to config.inc.php, located in root of calendar directory, and edit the following according to your requirements:
	* Change domain.ltd to your FQDN. 
	* If Nextcloud was installed using a custom directory, change /nextcloud/ in the URL structure to match the directory you installed in.
	* **IMPORTANT** - Change calendar_crypt_key to any random sequence at least 24 characters. Pwgen on linux run `pwgen -s 24'  
	* There are many customizable variables which can be changed to your suite your needs.  
3. Import the corresponding initial SQL schema (MySQL, Postgres) located in calendar/drivers/*/SQL/ folder to your Roundcube database.  
4. Add "calendar" to $config['plugins'] in your Roundcube main config file.  
5. Login to Roundcube, click on the Calendar Tab, give it 15-30 seconds to do its thang and you should be good to go.  

***VERY IMPORTANT***

Your username and password **must** be the same for Nextcloud and Roundcube to work properly.\
The Nextcloud account must be created and user must log into Nextcloud at least once before calendar will sync in Roundcube. Nextcloud does not create calendars until the initial login, so there will be no calendar for the Roundcube Calendar to find.\
There are no plans at this time to implement the use of different login usernames. \
There shouldn't be any issues if you create your users in Nextcloud using the exact username and password required to login to Roundcube. \
There are configurable parameters to alter your email for logins within Roundcube config that may help you out if you require something a little different.  \
Your roundcube and nextcloud must be run from same domain, no subdomains because of cross-scripting issues.  

**Known Issues**

* Will not create new calendar from Roundcube Calendar GUI.

**Help Wanted**

If anyone would like to help maintain and develop more features, I would truly appreciate it.

**Wishlist**

- [ ] Add the ability to create new calendar within Roundcube Calendar GUI.
- [ ] Oauth support for a wider range of calendar choices. (Probably will take me a month of Sundays as my skills aren't the best. :frowning_face:  ....  I need some help
- [ ] Add a preview / agenda list in main Mail Tab within the left side column at the bottom.
- [x] ~~Assign random colors upon initial sync of calendars.~~ - Thank you @drlight17
- [ ] Add sound notifications.
- [ ] Integrate a Caldav Enabled Tasklist plugin.
- [x] ~~Add Emoticon Support.~~ @texxasrulez
- [x] ~~Remove mcrypt and replace with openssl.~~ Thank you @MAT-WEISS-2017
* User feature requests are always welcome but I cannot guarantee if I can pull it off ... :relaxed:

**Submitting Issues**

Since this is a **USE AT YOUR OWN RISK** plugin, any submitted issues may or may not be attended to in any timely manner. I will be introducing bugs and fixing and back again. Issue Submitting is by all means totally welcome since details given by users will help me out ...

:moneybag: **Donations** :moneybag:

If you use this plugin and would like to show your appreciation by buying me a cup of coffee, I surely would appreciate it. A regular cup of Joe is sufficient, but a Starbucks Coffee would be better ... \
Zelle (Zelle is integrated within many major banks Mobile Apps by default) - Just send to texxasrulez at yahoo dot com \
No Zelle in your banks mobile app, no problem, just click [Paypal](https://paypal.me/texxasrulez?locale.x=en_US) and I can make a Starbucks run ...

I appreciate the interest in this plugin and wish nothing but the best for all ...
