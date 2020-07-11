# Setup Crafty

Now that you have installed Crafty, it is time to set it up!

## Post 3.0

The first time Crafty is run, it will ask the user a series of questions to help configure the product. The answers to these questions can be changed later if needed via the web console under the config area. These questions will be presented upon first login to the management interface, rather than in the console like previous versions.

!!! note "Are you using Docker?"
    If you are using Docker, you will not be asked these questions. To obtain the admin password, run Crafty in foreground mode first.

To log into the management interface, you will need to pen your browser and head to `https://<your server ip>:8000/` and log in with the username `Admin` and password provided in the Crafty console.

### Installer Options

| Question                                     | Description                                                                                                    | Default/Suggested (3.0 and above)     |
|----------------------------------------------|----------------------------------------------------------------------------------------------------------------|---------------------------------------|
| *What folder is your server jar located in?* | Enter here where you'd like Crafty to look for your *.jar when starting your server.                           | `/var/opt/minecraft/server`           |
| *What is the filename of your server.jar??*  | Enter the name of your server *.jar exactly as its written, this is what Crafty will look for to run.          | `paperclip.jar`                       |
| *Server **Maximum** Memory*                  | Enter the maximum amount of memory you'd like your *.jar to consume.                                           | `2048`                                |
| *Server **Minimum** Memory*                  | Enter the minimum amount of memory you'd like your *.jar to consume.                                           | `1024`                                |
| *Additional Arguments*                       | If you'd like your server.jar to be run with any additional arguments, enter them here.                        | n/a                                   |
| *Server Autostart*                           | If you would like your server to automatically start whenever Crafty is started, enter `y`. If not, enter `n`. | `y`                                   |
| *Autostart Delay*                            | If you'd like Crafty to wait a bit before starting your server, enter the time in seconds here.                | `10`                                  |
| *What port should the webserver run on?*     | Provide the port you wish to connect to the Crafty WebUI on.                                                   | `8000`                                |


## Pre 3.0

!!! danger "Why are you using an EOL version?"
    This version of Crafty is now obsolete and has reached End of Life, upgrade now!

The first time Crafty is run, it will ask the user a series of questions to help configure the product. The answers to these questions can be changed later if needed via the web console under the config area. 

The installer does have defaults for fields saved already that will be used if nothing is entered into the fields. Upon completion of the installer, Crafty will start up using the settings defined during the *Crafty configuration installer*. It will then wait for the user at the console to enter the exit command (or stop) and will continue to run until such a command is given. The installer will automatically create a username (Admin) and a random 6 character password. Please change the password immediately via the web console to something more secure, we recommend a truly random 6+ word passphrase (See https://xkcd.com/936/).

