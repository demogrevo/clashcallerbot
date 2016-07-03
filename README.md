# GroupMe Bot that uses Clashcaller

### Prerequisites:
 - This application was customized to run in Openshift (openshift.com) so you'll need an openshift account.
 - Install Ruby, Git, RHC and create an application by following the instructions here: https://developers.openshift.com/getting-started/windows.html  
 - In this step, you'll create a new application, and add NodeJS and MySQL cartridges. See link about for more details.
 - You will also need  to create a GroupMe bot. Watch https://www.youtube.com/watch?v=8wh_TRPCEsQ on how to do it.
 
 - Get the template code from your Openshift application source code. You'll find the source code url in OpenShift application page.
   As an example, lets say we created an application named ```"sandsnake"```, with the domain name ```"sss"``` in Openshift: 
 
```
c:\> mkdir bots
c:\> cd bots
c:\bots> git clone ssh://57718af289f5cf88c1000096@sandsnake-sss.rhcloud.com/~/git/sandsnake.git/
```

Note: this will create "c:\bots\sandsnake" folder.

- Get the bot source code from Github:

```
c:\> cd bots
c:\bots> git clone https://github.com/poweribo/clashcallerbot.git 
```

Note: this will create "c:\bots\clashcallerbot" folder

 - Copy all files from ```c:\bots\clashcallerbot``` into ```c:\bots\sandsnake folder``` (select all and copy paste), overwrite any file with the same name.
 - Delete server.js as you wont need it
 - Add yourself as the first bot Admin (Only admin can start wars, set timer, add other admins etc) 
  so find a way to get your GroupMe id and edit ```admin.txt``` to type in your GroupMe id. 
  i.e. Find a group with a working caller bot and type ```/me```.

  Any number of admins can be added. IDs should be separated by comma. Format should look like below example :
  
```
  ID_OF_ADMIN_1,ID_OF_ADMIN_2,ID_OF_ADMIN_3
```  

- Set environment variables for your openshift bot (this is just an example, provide your own application's name in place of "sandsnake".
Find your bot id from https://dev.groupme.com/bots and provide your own clan name.

```
c:\bots> rhc set-env OPENSHIFT_MYSQL_DB_NAME=sandsnake -a sandsnake
c:\bots> rhc set-env BOT_ID=abcdefghabcdefgh -a sandsnake
c:\bots> rhc set-env CLAN_NAME='Reddit Viper' -a sandsnake
c:\bots> rhc set-env CALL_TIMER=3 -a sandsnake
```

- To verify you have correctly set all the environment variables, do:

```
c:\bots> rhc env list -a sandsnake
```

 - After setting up the env variables, upload the files to openshift by doing:
```
c:\bots\sandsnake> git add .
c:\bots\sandsnake> git commit -m "initial commit"
c:\bots\sandsnake> git push
```

 - Thats it, your bot will be up shortly. To monitor the logs, do the ff below:
```
c:\bots> rhc tail -a sandsnake   
```   
 - Set up the database! Your application will look like http://sandsnake-sss.rhcloud.com/
   so to set up your database (to be done only once!), do that by going to: ```http://sandsnake-sss.rhcloud.com/setup``` using your browser
 - After setting it up, type ```/help``` in your GroupMe group to see the commands or ```/help -a``` to see commands including admin commands

### Creating admins ###
 - Assuming that you've set up the bot, and its working fine, its time to set admins.
 - If you have followed instructions above, you are the first admin. There is need to edit admin.txt to add more admins, 
   you can do it in GroupMe (if you are an admin)
 - Let other admin-to-be members to type ```/me``` in group to reveal their GroupMe ID (for example 12345559).
 - Copy that ID and type in GroupMe group: ```/add admin 12345559```. 
 
Credit: This bot is based on https://github.com/butttons/clash-caller. Thanks for the great bot!