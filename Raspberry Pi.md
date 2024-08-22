# Raspberry Pi

## What is it?

The Raspberry Pi is a small hobby computer that many people use to set up small home server applications. While the newer models may come with a 64-bit processor, the one I have has a 32-bit armhf processor, making it difficult to install docker and most server applications. 

## Using My Pi

My Pi is a Raspberry Pi 3 with an armhf running Raspbian, a variation of Debian built for these systems. 

### Commands

To run a terminal as root:

	sudo -I

To update to the newest version:

	sudo apt update
	sudo apt upgrade -y

If you need to see which Raspbian version you are using:

	lsb_release -a     ( -d will show only the description line)

### Resetting from the Base Image

Holding the space bar during bootup will trigger NOOBS ("New Out of the Box Software"), an application through which you can wipe the Pi back to factory. This is a great option when your current setup gets too overdrawn or you just need a reset.

After wiping the OS, this is my process to getting the PI back up to shape:

	sudo apt update
	sudo apt upgrade -y
	sudo apt autoremove

### Remote Connection

While I have a desk setup for my Pi (commonly called a "head"), I prefer to connect in from my laptop. You can use the following command to open the Pi Configuration program and allow remote connections

	sudo raspi-config

Navigate through Interface Options > VNC > Yes to authorize remote connection. If the remote window resolution is not what you want, you can change it by navigating Display Options > VNC Resolution > 1920x1080 (Or what you like).

To find the IP address of the Pi, you will want to run 

	hostname -I 

Once VNC is enabled and you have the Pi IP Address, you can use a [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/) on a different computer. Note that you will be asked for a username and password, which should have been changed, but by default is username pi and password raspberry.

### Other

Check out [this beginner's guide to Raspberry Pi](https://www.embeddedrelated.com/showarticle/1332.php)!
