_Below a guide for setting up LeJOS NXJ v.0.9 on Linux (Ubuntu 12.04) is demonstrated_

# Dependencies #

### JDK (Java Development Kit) ###
A major depencency for LeJOS to operate is JDK. Obtain it by:
```
$ sudo apt-get install openjdk-6-jdk
```

## LibUSB - bluecove ##

Obtain LibUSB by:
```
$ sudo apt-get install libusb-dev
```

#### Setup driver ####

_Setting up a catholic system setting for the driver is highly recommended_

  1. Create a file:
```
$ sudo nano /etc/udev/rules.d/70-lego.rules
```
  1. Add in:
```
# Lego NXT brick in normal mode
SUBSYSTEM=="usb", DRIVER=="usb", ATTRS{idVendor}=="0694", ATTRS{idProduct}=="0002", GROUP="lego", MODE="0660"
# Lego NXT brick in firmware update mode (Atmel SAM-BA mode)
SUBSYSTEM=="usb", DRIVER=="usb", ATTRS{idVendor}=="03eb", ATTRS{idProduct}=="6124", GROUP="lego", MODE="0660"
```
  1. Save
  1. Add a new group called "lego"
```
$ sudo groupadd lego
```
  1. Add your user to "lego" group
```
$ sudo gpasswd -a <user> lego
```
  1. Reboot

# Obtain LeJOS #

  1. 'cd' in your home directory
```
$ cd /home/<user>
```
  1. Download LeJOS (0.9.1beta)
```
$ wget http://sourceforge.net/projects/lejos/files/lejos-NXJ/0.9.1beta/leJOS_NXJ_0.9.1beta-3.tar.gz 
```
  1. Untar it in /opt and rename
```
$ sudo tar xvf leJOS_NXJ_0.9.1beta-3.tar.gz /opt/ && cd /opt && sudo mv leJOS_NXJ_0.9.1beta-3/ leJOS_NXJ/
```
  1. Build
```
$ cd /opt/leJOS_NXJ/build && ant
```

# Environment variables #

leJOS NXJ needs to know the locations of _java_ and _javac_. There are several possibilities to achieve that: (1) add the bin directory of the JDK to your _PATH_ environment variable so that commands such as java and javac can be called from a command prompt or (2) set the _LEJOS\_NXT\_JAVA\_HOME_ environment variable to the directory of an installed JDK. Note that you can use JAVA\_HOME instead of _LEJOS\_NXT\_JAVA\_HOME_, however setting _JAVA\_HOME_ might intefere with other applications.

Furthermore, the _NXJ\_HOME_ variable should be set to the directory where leJOS NXJ is installed. It allows other applications, e.g. the Ant scripts, to locate the leJOS Development Kit. Also, for easy exececution of the leJOS commands on the command line, the bin folder of the leJOS distribution should be added to the _PATH_ variable.

Examples:
#### in /etc/profile ####
```
$ sudo nano /etc/profile
```
```
variable=location
```

|Variable | Value | Examples |
|:--------|:------|:---------|
|NXJ\_HOME | The folder you installed leJOS NXJ into | /opt/leJOS\_NXJ |
|LEJOS\_NXT\_JAVA\_HOME | The folder where the JDK is installed | /opt/sun-jdk-1.6.0.30 _or_ /usr/lib/jvm/java-6-sun-1.6.0.06 |
|PATH     | Prepend the bin of the leJOS Development Kit | opt/leJOS\_NXJ/bin:$PATH |

## Using Eclipse IDE Plugin ##
[Click here](http://lejos.sourceforge.net/nxt/nxj/tutorial/Preliminaries/UsingEclipse.htm).

# Flash Firmware #

  1. Connect your NXT via USB to the PC
  1. Power on
  1. Execute
```
nxtflashg
```
  1. Tada!

# Troubleshooting #

  1. You must reset your NXT Intelligent Brick by pushing the small button at the rear of it with a screwdriver, unless you're able to flash the leJOS firmware.