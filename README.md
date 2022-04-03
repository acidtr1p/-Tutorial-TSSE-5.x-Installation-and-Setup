# -Tutorial-TSSE-5.x-Installation-and-Setup

Attention
if this is your first time installing TSSE I recommend you read this, also you require to read everything from the installation steps, and have at least 1 hour to play around tracker settings to get familiar with if you fail to do that YOU WILL HAVE problems with setup.
Even if you read everything there is still a high chance having issues




(NOTE: there are other ways of doing this so if you're an expert you'll figure out on your own except for few steps)

Basic Setup

1. Unzip the release archive to your computer using an archive utility capable of decompressing the download format you choose (Winrar,Winzip).

2. Using an FTP client (FlashFXP,CuteFTP), upload the entire contents of the 'upload' directory to a visible directory on your web server.

3. CHMOD the following files/folders to 0777 (ie, make sure that PHP can write to them).
- ./config/
- ./config/CLEANUP
- ./config/DATABASE
- ./config/DATETIME
- ./config/EXTRA
- ./config/FORUMCP
- ./config/KPS
- ./config/MAIN
- ./config/PAYPAL
- ./config/PJIRC
- ./config/REDIRECT
- ./config/SECURITY
- ./config/SEO
- ./config/SMTP
- ./config/STAFTEAM
- ./config/TWEAK
- ./config/THEME
- ./config/WAITSLOT
- ./torrents/
- ./torrents/images/
- ./include/avatars/
- ./tsf_forums/uploads/
- ./admin/backup/
- ./cache/
- ./cache/funds.php
- ./cache/indexstats.php
- ./cache/systemcache.dat
- ./cache/massmail_config.php
- ./admin/ads.txt
- ./admin/adminnotes.txt
- ./admin/quicklinks.txt
- ./include/config_announce.php

4. In your browser, visit the URL where you installed your tracker, appending ./install/install.php on to the end of it.

5. After the installation has completed, please DELETE the 'install' directory from server.

6. You can now login to the Administration Control Panel by appending ./admin/settings.php on to the URL of your tracker.

IMPORTANT: Do not forget to protect your ./CONFIG folder by using apache config.
Example httpd.conf

<Directory "C:/wamp/www/yourtrackerfolder">
Options -Indexes +FollowSymlinks +MultiViews -SymLinksIfOwnerMatch
AllowOverride all
Order Allow,Deny
Allow from all
</Directory>

7. it's recommended to backup your /config/ folder now before changing any information in tracker settings.

8. Make sure you go over EVERY EVERY EVERY detail on Tracker Settings 

--- End of Basic Setup ---


Multi Language Setup
Note: this is only helpful for non-latin languages like Arabic, Greek, Russian, Hebrew
1. figure out if UTF8 covers your language or you can choose the proper ISO however UTF8 usually works well with many languages so it's a very good option
2. this is debatable of which collation should be used on your SQL server, some of the recommended utf8_bin, utf8_unicode & utf8_general however you can use your own ISO code e.g. cp1256
3. Setup the tracker described in basic setup
4. Assuming we'll be using utf8 go to your "Tracker Settings" --> "Theme and Language settings" --> set both character sets to UTF-8
5. now you can use another language pack or you can create your own
6. if you're still using UTF8 and wants to stay with it make sure that all your language files are written in unicode if not do so
7. Right to Left languages? it's hard to setup you need to test out each language file to see if it looks ok on the site

-Here are the debates-
to stay with your localized ISO or go to UTF?
1. here is what I think, if the language pack you downloaded is already in whatever format and you don't want to change its encoding then just follow that i.e. if unicode compatible or your other chosen encoding
2. if fresh made up language files then you can also decide about that but I warn you that the file list tab on torrent details page might not show up properly unless user manually change the View encoding to unicode but other than everything probably would work ok
3. byte size? UTF8 vs ?? google that :)

-End of Multi Language Setup-



FAQ

Q. I'm having IONcube problems?
A. Did you google? check this How to install ionCube loader

Q. I can't install I'm getting Internal Server Error 500
A. 1. Your host setup is improper, 2. you're using subdomain and main domain .htaccess is interfering, 3. you can try to delete off htaccess from your domain 

Q. I can't access staffpanel, what did I do?
A. because you forgot to setup the pincode in "tracker settings" also it's reported you need 5-7 long pin and it's better just to use numbers

Q. how can set my users to use the shoutbox?
A. again GO BACK to tracker settings, 2 spots to fix in usergroup permissions and plugins permissions

Q. I tried to upload a torrent but it didn't work?
A. it looks like site only work when the "Private Patch" activated in tracker settings, which means each torrent has passkey on the end of announce URL which is different for every user. i.e. after uploading a torrent you should download the torrent file again from site to start seeding! also did you forget to CHMOD torrent folder?

Q. I tried to upload an image with the torrent but it didn't work what's wrong?
A. did you forget to CHMOD the image folder in /torrent/? also maybe your GD on your host not working or outdated? also it looks like not all jpegs can be read by the script however screenshots created by MPC should work fine

Q. I can't make new moderators and admin they get "we believe you're using fake account...." what to do?
A. for each new staff member has to be added in "Tracker Settings" --> "Manage Staff Team" in there you have add the appropriate info ( I recommend that you backup /config/STAFFTEAM before trying anything)

Q. would there be a bug even after installing everything properly?
A. Yes there are bugs that you can't do much about unless somebody debug them. always search the forums if there are any fixes offered on the forums or even better help in fixing the bugs

Q. I have more questions!!!
A. PLEASE use Search function before asking, your question is probably been asked before so look for answers first then try to open a new topic

I will add more to this sometime

I hope you find this helpful 


Cheers

(NOTE to other mods and admins feel free to edit)
__________________
