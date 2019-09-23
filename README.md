
# andesite-server-main
The main and default server for andesite.

This readme document will guide you through it's workings.

# Let's start with the basics.

Andesite is created to keep simplicity and the modular design formular at it's best. If users wan't to add, for example, a third party API, they are free to do so while not being able to pirate games due to the safety implementations in there. Here are some of Andesite's best features.

## Flexability.

Andesite can directly store executables as both binaries or source on the server, depending on how the software/game is licensed and/or it is open source. This can save a ton of space and garantuees the integrity for the users.

## Update a game while it's being played, for many engines.

Users will be able to play a game while it's being updated or downloaded. Games have to be specially programmed to be playable while an download is occuring, but updating works on the current engines (tested, at least)

 - Game Maker: Studio 1.4 **or** Game Maker: Studio 2
 - Unity3D
 - Godot

Programmers will be able to add support themselves too. 

## External Storage seperated from the main one? Easy.

You can link your CDN or Storage server to this server program. Games can also be stored on the server the program is running on. Just make sure to follow the file structure guidelines.

# Guidelines for set-up and keeping it running
This is the most important part for you. Take your time reading this in detail.

## File structure

Always make sure your server follows the expected file structure. That means:

- Keeping your games in /downloader/[APPID]/
- Keeping your AppIDs and dependency list in /database/appid.xml
	- The xml has to follow the example document, so
		- It has to have the Game's name to be displayed
		- Minimum requirements / Recommended requirements
		- Your preferred DRM method.
		- App version


## Backup/Emergency server

In order to prevent a chatastrophic system failure, make sure you're running **multiple** of these backup servers that give users the basic functions. For example:

- Keep the DRM service alive
- Keep chatting-services alive
- Make Users' session files not expire
And, additionally, 
- Offer a backup CDN

There are two ways to run the emergency-servers:

- Run one on an external service like AWS, Google Cloud Computing or Heroku.
	> We **do not** advise to keep an download network on an free solution. Just keep your chat there, keeping your DRM would be a death sentence.

- On an usual Linux server
	> Note: It may be different to run on some Distros compared to others. Debian requires a whole other process than, for exmaple, Fedora

## Set-up

Just make sure Python3 is installed to run the included setup.py file.

>Debian: sudo apt-get install python3 python3-pip

>Fedora/RedHat: sudo dnf install python3 python3-pip

Then `sudo python3 setup.py` and wait. It will install all dependencies. It may ask for your sudo password though.

## Expandability
You can expand on Andesite using the [Docs](https://google.com).
The basics are as follows (for a bot service to automatically do actions):
import andesite.chat

    def MODULENAME:
    	if andesite.chat.messagenewest == "!hello":
    		andesite.chat.sendtonewest("Hello!")
    
    andesite.chat.module("MODULENAME")

As you can see, pretty easy!


