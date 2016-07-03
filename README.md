# GroupMe Bot that uses Clashcaller (Clash of Clans target caller)

### Prerequisites:
 - Install Ruby, Git, RHC and create an application by following the instructions here: https://developers.openshift.com/getting-started/windows.html 
 
```
$ git clone https://github.com/poweribo/clashcallerbot.git 
```
 - Go into directory:
```
$ cd clashcallerbot
```
 - Login into heroku:
```
$ heroku login
```
 - Create the app:
```
$ heroku create
```
 - This will return a link to your heroku app. Copy that. The link will be like:
```
https://XXXXXX-XXXXX-XXXXX.herokuapp.com/
```
  - Creating a database:
```
$ heroku addons:create cleardb:ignite
```

 - Go to [GroupMe Developer Website](https://dev.groupme.com/) and log in using your GroupMe details.
 - Go to [GroupMe Bots page](https://dev.groupme.com/bots) and click on 'Create Bot'.
 - Set the group the bot will reside in, its name, and in the *Callback URL* field, put the heroku app link you got from above step (https://XXXXXX-XXXXX-XXXXX.herokuapp.com/)
 - Submit, you will be redirected to the bots index page. Copy the *Bot ID* of your Bot from here.
 - Go to your project folder (**caller-bot**) and edit the following files:
 - ``` .env``` file. Put your bot ID there like:
```
BOT_ID="YOUR_BOT_ID_HERE"
```

 - Call timer values for settings:
```
0: none
-2: (1/2) flex timer
-4: (1/4) flex timer
1: 1 hour
2: 2 hours
3: 3 hours
4: 4 hours
5: 5 hours
6: 6 hours
7: 7 hours
8: 8 hours
9: 9 hours
10: 10 hours
12: 12 hours
24: 24 hours
```

 - ```clash_caller.js``` file for clan name (line 17) and call timer (line 18) settings:
```javascript
var my_clan_name = "Your clan name here"; // Line 17
var war_call_timer = 6; // Line 18, in hours
```
 - In terminal, in your directory where you made the app, create a config variable on heroku using:
```
heroku config:set BOT_ID='YOUR_BOT_ID_HERE'
```
 - After setting up the variable, upload the files using:
```
git add .
git commit -am "first push"
git push heroku master
```
 - Thats it, you're bot is up. Only thing is to set up the database. Do that by going to: ```https://XXXXXX-XXXXX-XXXXX.herokuapp.com/setup```
 - After setting it up, type ```/help``` in your group to see the commands. You need to add admins before you put change default caller code. If you have an exisiting clash caller going on type ```/set cc (code)``` to save it. To create new clash caller type ```/start war (war size) (enemy name)```
 - Go to the following routes to do the actions:
```
/setup - to set up database
/cc - to view current caller
/log - to view log
```

- - -

### Creating admins ###
 - Assuming that you've set up the bot, and its working fine, its time to set admins.
 - Type ```/me``` in group to reveal your GroupMe ID.
 - Copy that ID and paste it in ```admins.txt``` file in csv format. Any amount of admins can be added. The format is:
```
ID_OF_ADMIN_1,ID_OF_ADMIN_2,ID_OF_ADMIN_3
```

 - Now that its done, push these changes using:
```
git add .
git commit -am "setting admins"
git push heroku master
```
