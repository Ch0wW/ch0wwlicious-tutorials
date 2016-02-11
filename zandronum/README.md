# How to create a Zandronum server on Linux

This readme contains a tutorial, in order to create a remote Zandronum server, the simpliest as possible.
We will use a Linux - Debian distribution. You can use Ubuntu, or Linux Mint with no problem.

Here are the steps that we will do:
- Create an user specifically for Zandronum
- Install Zandronum
- Configure the folders
- Run it!
- Get some templates


##Pre-Requisites

In order to make this tutorial painless, you will need the following:
- Your Doom IWAD in UPPERCASE (DOOM.WAD, DOOM2.WAD, TNT.WAD, PLUTONIA.WAD) -- That's my reference to find my IWADs.
- A FTP client to transfer files. FileZilla can be a nice choice.
- A SSH client to remotely control the server. Grab PuTTY!

##Let's start everything up!

>You currently are logged in with the "root" account!!!

We will create an user called doomuser. Type this command:
>adduser --force-badname doomuser 

It will ask for a password. Put one.

Why have we done that? If the Zandronum server is run by a superadmin account (such as root) and is exploited, you can make your system suffer badly. <br />
So, we'll prevent it by creating a safe user account.

## Let's install Zandronum now!

There are 2 ways to install zandronum: either by compiling the sources, or by automatically get the official package.

Since we aren't willing to put much work to install Zandronum (unless you really wish to add personnal features), we are going to install it automatically.

Type these commands (taken from the official page):
>add-apt-repository 'deb http://debian.drdteam.org/ stable multiverse' <br />
wget -O - http://debian.drdteam.org/drdteam.gpg | sudo apt-key add - <br />
sudo apt-get update <br />
sudo apt-get install zandronum-server -y

Since Zandronum is not on any official sources from Debian/Ubuntu/Linux Mint, we are adding the official one from the team, so that installing would be much easier. And that is!

## Configure the folders

Since the installation is done, we will now make the folders for the user doomuser. 
But first, let's log in as doomuser!

> su doomuser

Put the password you used earlier.

Now, we will create a folder called "zandronum" for our WADs and configuration files.

> mkdir $HOME/zandronum <br />
cd $HOME/zandronum

With your FTP client, put your IWADs within that folder.

## Run it!

> We are still with doomuser, in $HOME/zandronum !!

Since we have put everything important, let's make a check to see if Zandronum is actually working. Type in this command:
> zandronum-server -iwad DOOM2.WAD

It should load MAP01 (or E1M1 if you put DOOM.WAD), as seen in this picture:


If an error says it hasn't found any IWAD, check if you put the wad in uppercase, as said above. Otherwise, good job! You have managed to do the hardest!

## Get some templates!

Now that we know our server works, why not customizing it? 

Lucky you, I have a template ready for deployment.

> We are still with doomuser, in $HOME/zandronum !!

Type these commands:

> wget ?????????????? <br />
wget ???????????????? <br />
chmod 750 ./server.sh

Now, with nano, open the file. Modify what you need (while still respecting the template!). 

Once it is done, write this command:
./server.sh

If it still goes well, your server appears! Congrats, you are a pro at making Zandronum servers!