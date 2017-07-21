# Setting up a dev environment for QMK on a Windows 10 PC

FIRST: Read through https://docs.qmk.fm/build_environment_setup.html for an idea of what's going on.

Get the following

* Virtualbox https://www.virtualbox.org/
* Vagrant https://www.vagrantup.com/
* Git Bash  https://git-scm.com/download/win

Install them all

Start git bash

At its command prompt, type
```
	vagrant init bento/ubuntu-16.04
	mkdir firmwares
```
Get your current working directory
```
	pwd
```
In Windows Explorer, browse to that directory.

Look for a file named 'Vagrantfile'

Open it, but be sure to use Notepad.exe -- otherwise you'll mess up your line endings.

Look for a line like
```
	# config.vm.synced_folder blah blah
```
Change that to 
```
	config.vm.synced_folder "firmwares", "/firmwares"
```
Save that file, and close Notepad.

In git bash again, run
```	
	vagrant up
```

That will get you a little baby Ubuntu Linux box.

SSH into it:
```
	vagrant ssh
```
You should be at a new prompt, inside your VM.

Play with it a bit. Go through http://www.tldp.org/LDP/intro-linux/html/chap_02.html , for 15 mins or so. 

On your VM, run
```
	sudo apt-get update
	sudo apt-get upgrade
	#(tell it yes for whatever)

	sudo apt-get install -y git make virtualbox-guest-additions-iso

	git clone https://github.com/qmk/qmk_firmware.git

	cd qmk_firmware
```
This directory is where your firmware files will be found, after you build them.

Next run
```
	sudo ./util/install_dependencies.sh
	# don't forget that dot!
```
When it's done installing all the dependencies, run
```
	cd keyboards/whatever_your_pcb_is_based_on
	make
```
It may complain some, but it'll eventually create the .hex files for all the keyboard layouts listed in the layouts/ subdirectory here. 

The firmware files will be "up" two directory levels from where you are, so, run
```
	cd ../../
```
Now you should be in 'qmk_firmware'
```
	pwd
	# should show you something like /home/sumthin/qmk_firmware
```
Look for your firmwares
```
	ls *.hex
	# should show many hex files
```
Copy them all to your shared Windows firmware directory
```
	cp *.hex /firmwares/.
```
Now, in Windows Explorer, look in that same directory you looked in at the beginning, with the Vagrantfile.

You should see a folder called firmwares. Inside is your hex files!

Now you can use the QMK Firmware Flasher ( https://github.com/qmk/qmk_flasher ) to flash your board. 

