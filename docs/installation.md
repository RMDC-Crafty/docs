# Installation

## Supported Platforms

!!! info "Where's my distro?"
    If the distro/OS that you use is not on the list, sign up to become a Tester by joining the [Discord Server](https://discord.gg/S8Q3AKb) and we'll help you install Crafty.

|   OS Name      |    Version(s)      |  Installation Method  |
|:---------------|--------------------|-----------------------|
| Ubuntu         | 18.04 and 20.04    | [Linux Installer](#linux-installer)    |
| Debian         | 9 and 10           | [Linux Installer](#linux-installer)   |
| MacOS          | 10.14+ (with Brew) | [MacOS Installer](#installation-on-macos)    |
| Windows        | 8 and 10           | [Windows Installer](#installation-on-windows)  |
| Windows Server | 2016 and 2019      | [Windows Installer](#installation-on-windows)   |
| Other          | Any                | [Docker Install](#install-using-docker) |

!!! warning "Ensure your MC Server is operational"
    Crafty as with all server managers requires your server to be in a operational state. That means the Eula.txt and world folders are already created and in the same folder as your .jar file. Don't try to run Crafty with only a jar file in your server folder, it will crash.

## Installation on Linux

### Linux Installer

We recommend you use the Linux installer to install Crafty on your linux machine. It will gather most dependencies and install Crafty with minimal user intervention.

#### Install the required packages

```bash
sudo apt install git python3 python3-pip python-dev -y
```

#### Download and Run the Crafty Installer

```bash
git clone https://github.com/rmdc-crafty/installer-linux.git 
cd installer-linux
sudo bash ./install_crafty.sh
```

!!! info "Crafty is not setup yet!"
    After you have followed the prompts to install Crafty, head over to the [setup] page

### Install from Source

!!! danger "Only for devs and experienced users!"
    Crafty install from source is not recommended, as it is a very complicated and long-winded procedure. If you are new to Linux systems and/or lacking in experience with Python environments, please use the [Linux Installer](#linux-installer)!


#### Requirements & Assumptions

* You have sudo and can install software
* This guide assumes you have a decent understanding of a Linux environment and are comfortable with the command line.
* This guide also assumes you will be installing Crafty into `/var/opt/minecraft/crafty`.
* We also assume your server will be at `/var/opt/minecraft/server`.
* We also assume the user account running crafty will have full read/write/execute permissions on these folders.
* This guide will instruct you how to setup a service account for Crafty as well.

#### Install Required Packages

On Ubuntu/Debian variants, you can install required software via the command line by typing:

```bash
sudo apt install git python3.7 python3.7-dev python3-pip software-properties-common
```

#### Create a directory for Crafty

Let’s make crafty a place to live on your server.
This guide will use `/var/opt/minecraft/crafty` as it’s example.

```bash
sudo mkdir -p /var/opt/minecraft/crafty
```

#### Create a Crafty User Account

```bash
sudo useradd crafty --system --no-create-home
```

#### Setup permissions for the folders

*You can setup whichever group you wish, but this guide uses nogroup.*

```bash
sudo chown crafty:nogroup -R /var/opt/minecraft/crafty
sudo chown crafty:nogroup -R /var/opt/minecraft/server
```

#### Get the source

```bash
cd /var/opt/minecraft/crafty
git clone https://gitlab.com/Ptarrant1/crafty-web.git
```

#### Create the Virtual Environment

Install the required pip package.

```bash
sudo pip3 install virtualenv
```

Create the virtualenv and activate it.

```bash
virtualenv venv
source venv/bin/activate
cd /var/opt/minecraft/crafty/crafty-web
```

#### Install all the things / requirements

```bash
pip3 install -r requirements.txt
```

#### Ensure Java is installed

!!! info 
    We will be using the standard java build distributed in most main package repositories here. If you want to use the proprietary Oracle java builds, please install the correct PPA and replace the package name below with the desired alternate package name.

```bash
sudo apt install openjdk-8-jdk opendjdk-8-jre
```

#### Run Crafty

```bash
python crafty.py
```

**That’s it! Crafty should now be running and asking some install questions.**

## Installation on Windows

### Pre-compiled Executable

#### Get the latest build

Head over to our website <https://craftycontrol.com/#download> and click the **Windows Portable Install** download button.

#### Unzip Crafty

Once Crafty has downloaded, extract the ZIP file to the directory you want Crafty to exist in.

#### Run Crafty

All you now need to do is double-click `run-crafty.bat`. A new window should now appear asking some questions, follow the prompts to setup.

## Installation on macOS

These instructions will guide you to install Crafty on macOS.  This guide was built taking macOS Catalina 10.15.2 in mind, but it should work for the most part in macOS Mojave 10.14.6 and macOS High Sierra 10.13.6.  Anything older it probably won't and we won't cover it here.

### Installation from Source

#### Requirements & Assumptions

* You will need brew.sh installed in your mac. Get it from [https://brew.sh](https://brew.sh)
* This guide assumes you have a decent understanding of the macOS Terminal environment and are comfortable with the command line.
* This guide assumes you will be installing Crafty into `/var/opt/minecraft/crafty`.
* This guide assumes your server.jar is located in `/var/opt/minecraft/server`.
* We also assume the user account running crafty will have full read/write/execute permissions on these folders.

#### Install Pre-Requisites

##### Brew.sh

macOS lacks a proper package manager and in order to install a couple of the required software via the command line you will need Brew.sh.

Go to your `/Applications/Utilities` and launch Terminal.app or press Command+Space and type Terminal.app and hit return/enter key.  Then paste the line below:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

The command above runs and you will see the installation progress.  It will inform you that the *Command Line Tools for Xcode* will get installed. 

Towards the end you will be asked to enter your *account password* then the installation will continue.

You will be notified when Brew begins downloading the *Command Line Tools for Xcode* and depending on your connection the download will take about 5 minutes.  Once the tools have downloaded, they will install on your mac and the installation of Brew will be completed.

##### Installing Pre-Requisite Packages

Install all of the required packages

```bash
brew install git python3
brew cask install java
pip install --upgrade pip
```

#### Create a directory for Crafty

Let’s make crafty a place to live on your server. This guide will use `/var/opt/minecraft/crafty` as it’s example:

```bash
sudo mkdir -p /var/opt/minecraft/crafty
```

#### Setup permissions for the folder

```bash
sudo chown <your_username>:admin /var/opt/minecraft/crafty
```

**For Example** If your username on your mac is **Totoro** then the command will be: 
`sudo chown totoro:admin /var/opt/minecraft/crafty`

#### Change to the Crafty dir

```bash
cd /var/opt/minecraft/crafty
```

#### Create a virtual environment "venv"

```bash
python3 -m venv venv
```

#### Clone Crafty Repo

*Please be sure to be in the `crafty` folder before cloning the repo.* To check type `pwd` and make sure it says `/var/opt/minecraft/crafty` before you continue.

```bash
git clone https://gitlab.com/Ptarrant1/crafty-web.git
cd /var/opt/minecraft/crafty/crafty-web
git pull
git checkout snapshot
```

Let's go up one directory

```bash
cd ..
```

#### Activate the Virtual Environment

Lets activate the Virtual Environment

```bash
source venv/bin/activate
```

your prompt will change to `(venv) whateveryourprompt is:`

#### Go into the crafty-web folder that was cloned down

```bash
cd /var/opt/minecraft/crafty-web
```

#### Install all the things / requirements

```bash
pip install -r requirements.txt
```

#### Run Crafty

```bash
python crafty.py
```

**That’s it! Crafty should now be running on macOS Catalina and asking some install questions.**

## Install using Docker

### Prerequisites

1. The latest Docker version, you can get it [here](https://www.docker.com/get-started)
2. The latest version of [docker-compose](https://github.com/docker/compose)
3. `git` installed on your system

### Installation

First, lets clone the crafty-web repository to the directory you want. For this tutorial, I will be using `/opt/minecraft`.

Open up a shell window and type:

```bash
mkdir /opt
cd /opt
git clone https://gitlab.com/crafty-controller/crafty-web.git minecraft
cd minecraft
git checkout snapshot
```

Next, put your minecraft server JAR's into `docker/minecraft_servers`. 

Once that is done, run the container

#### Foreground Mode

```bash
docker-compose up
```

#### Background Mode

```bash
docker-compose up -d
```

Then just access crafty as you normally would. When specifying the minecraft server directory, please use `/minecraft_servers`
