Starting Crafty can change depending on your operating system and setup. However, these are the normal ways:

## Windows
*  After downloading and extracting crafty, double click `run_crafty.bat` in the folder. 
*  Crafty is required to run from the same folder as it’s libraries and other resources. 
*  This batch file will automatically CD into the correct directory (`crafty`) and run crafty.exe. If you wish, you can do this yourself via a command line interface.

## Linux
We recommend you use some sort of terminal windowing service to allow Crafty to continue running even after closing your terminal session (for instance, when connected to your server over ssh). We've written instructions for two popular applications, screen and tmux.

#### Via Screen
1. From a terminal type `screen -S crafty` and press enter.
   - This will create a new screen session called *crafty*.
2. `cd` into the directory where crafty has been installed to, for example `/var/opt/minecraft/crafty/web-crafty`.
3. Now enter `run_crafty.sh` and press enter.
4. Crafty will now launch.
5. You can *detach* from this screen session by pressing `CTRL+A+D`
   - You can reattach to this screen (for instance to quit Crafty) by typing `screen -R crafty`.

Read more about *screen* [here](https://hostpresto.com/community/tutorials/how-to-use-screen-on-linux/).

#### Via tmux
1. From a terminal window type `tmux` and press enter. 
   - You will now see a terminal interface, but you are inside the tmux server. 
2. `cd` into the directory where the crafty repository has been cloned to (example: `/var/opt/minecraft/crafty/web-crafty`). 
3. Now run `./run_crafty.sh` from Tmux. 
4. Crafty will launch. Once Crafty is finished launching, you can then “detach” it by pressing `CTRL+B` and then `CTRL+D` to detach the window. 
   - To re-attach the window type `tmux attach 0`. 

You can read more about *tmux* [here](https://thoughtbot.com/blog/a-tmux-crash-course).

#### Auto-start Crafty on re/boot
Currently, Crafty must be started manually every time you turn on your machine. While we are working on making Crafty run as a service, you can [follow the instructions listed here](https://gitlab.com/Ptarrant1/crafty-web/issues/22#note_255441321) to make Crafty start automatically on boot.

#### Post 3.0
You can specify the `-d` option when running `crafty.py`, daemonizing it. 
```bash
python crafty.py -d
```

There is also a service configuration file located under `configs/`, which can be utilized by passing the `-c` option when running `crafty.py`. **This will disable the console in Crafty**
```bash
python crafty.py -c configs/service_config.yml
```

