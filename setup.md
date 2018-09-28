# James' Big Raspberry Pi Wildlife Camera Project

## Part One - Set up the Raspberry Pi

### Obtain Raspbian operating system and load onto micro SD card.

#### Parts
* Computer (running Ubuntu Linux, with internet access)
* Micro SD card
* Micro SD card reader

#### How to
* On computer search up www.raspberrypi.org.
* Download ‘Raspian Stretch’ (not NOOBS or LITE).
* Choose the ‘Download ZIP’, and choose ‘Save File’.
  * It will take a few minutes to download – you might have to go and get a drink while you are waiting.
* Find where the zip file is saved. Try looking in your ‘Downloads’ folder.
* Right-click on the zip file and choose ‘Extract Here’.
* Find the extracted ‘.img’ file in your Downloads folder.
* Insert the micro SD card into the card reader.
* Plug the card reader into a USB port on the computer.
* Ignore all the windows that pop up.
* Right-click on the ‘.img’ file and choose ‘Open With Disk Image Writer’.
* In the ‘Restore Image’ window select the micro SD card as the destination.
* Click Start Restoring...
  * You will probably need an admin to authenticate.
  * This will take a few minutes.
  * Don’t unplug anything.
* Eject the disk by right-clicking on the icon and selecting ‘Eject Parent Drive’.
* Unplug the card reader from the computer.
* Push the micro SD card to remove it from the card reader.
* Put the card reader away.

### Connect and power up the Raspberry Pi

#### Parts
* Micro SD card with Raspbian operating system
* Raspberry Pi 3 Model B
* Screen with HDMI cable
* USB keyboard and mouse
* USB power cable (type A plug to type micro B plug)
* USB mains adapter (type A socket)

#### How to
* Insert micro SD card into the socket on the Raspberry Pi.
* Plug the keyboard and mouse into any USB (type A) sockets.
* Plug the HMDI cable into the HDMI socket.
* Plug the USB cable micro B plug into the power socket.
* Plug the USB cable A plug into the mains adapter.
* Plug the mains adapter into the wall socket.
* Turn the monitor to its HDMI input.
* Power on the wall socket.
* BOOM!
* Check that the power LEDs light up on the Raspberry Pi
* The display should show some stuff and a reboot message may show briefly.
* Eventually the desktop image should load and stop.

### Set up the Raspberry Pi

#### Parts
* The Raspberry Pi setup.

#### How to
* Connect to the wireless local area network (WLAN).
  * Right-click on the network symbol (red crosses) and select your WLAN from the list.
  * You will have to ask the owner for the password.
* Click OK and wait for a connection.
* Update the Raspberry Pi operating system.
  * Open a terminal and type:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
  * You may have to enter a password, and answer a few questions. And wait a while.
* Click on the raspberry icon and select 'Preferences', and then 'Raspberry Pi Configuration'.
* On the System tab:
  * Boot To Desktop as the Current User.
- [x] Autologin [x]
  * [x]Wait for Network [x]
  * Disable the Splash Screen
On the Interfaces tab:
Enable Camera so we can take pictures – yay!
Enable VNC so that we can access the Pi remotely.
On the Localisation tab:
Set Locale to English (language), GB (country), and UTF-8 (character encoding).
Set Timezone to Area: Europe, Location: London. Close enough.
Check the time display changes to now!
Reboot the Raspberry Pi.

### 4. Access the Raspberry Pi Remotely. Virtual Network Computing (VNC).

#### Parts:
The Raspberry Pi setup
Daddy’s computer.

#### How to:
With the Raspberry Pi running open a terminal to access the Command Line Interface – or CLI. Click on the terminal icon at the top of the screen.
Enter the following commands one at a time pressing Enter after each line.
sudo apt-get update
sudo apt-get install real-vnc-server real-vnc-viewer
This will check that you have the latest versions installed. You may have to answer a few questions. Just type Y for yes.
Sign into RealVNC account on the Raspberry Pi: click on the VNC symbol at the top of the screen, click on the menu icon, and select ‘Licensing...’ from the menu.
Use the option ‘Sign in to your Real VNC account’.
Sign in using Dad’s VNC account. Username is . Password is’.
Choose ‘Connectivity method’ of ‘Direct and cloud’.
Click OK to any warnings.
Click next until you are sorted.
Now back on Dad’s computer start VNC Viewer from Dash Home. You might have to log into Dad’s VNC account.
Right-click on ‘raspberrypi’ in ‘Simon’s Team’ and click ‘Connect...’.
Click Continue at the identity check and log in to the Raspberry Pi. Username ‘’ (not ), password’.
If it all works you should now be looking at the Raspberry Pi desktop on Dad’s computer. Amazing.
Shut down the Raspberry Pi remotely from Dad’s computer, and power it off at the wall.
Unplug the keyboard, mouse and HDMI cable, and put them all away. We don’t need them any more.
Power up the Raspberry Pi again – this is what they call ‘headless’ because there’s no screen. You should be able to place the Raspberry Pi anywhere in the house and still connect to it using VNC from Dad’s computer. Try it.
You might have to adjust the screen resolution from the Preferences window. I used ‘DMT mode 82’ and it seemed to work OK. You have to reboot for the change to take effect. Of course this will lose the VNC connection so you will have to connect again.

### 5. Connecting the Raspberry Pi camera and taking a photograph.

#### Parts
The Raspberry Pi setup (without keyboard, mouse, or HDMI cable).
Daddy’s computer.
The Raspberry Pi camera module V2.1
The Raspberry Pi camera cable

#### How to
Connect to the Raspberry Pi remotely via VNC and shut it down. Turn it off at the wall. Disconnect the micro USB cable if it is easier.
Connect the Raspberry Pi camera cable to the Raspberry Pi. Use the white socket between the HDMI output and the headphones output. The shiny side of the cable connection faces the HDMI output connector.
Connect the Raspberry Pi camera cable to the Raspberry Pi camera. The shiny side of the cable faces the camera lens side.
Power on the Raspberry Pi and connect using VNC. Remember to plug the micro USB power cable in again.
The camera has already been configured. Open a CLI terminal and type:
raspistill -v -o test.jpg
There will be some text on the terminal screen and after a few second the command line prompt ‘$’ should reappear. Nothing seems to have happened but...
…if you open the file browser (the folders icon at the top of the screen) you should see a new file called ‘test.jpg’. Double click that file and it should show a picture you just took with the camera.

### 6. Install the ‘pikrellcam’ software to take motion-triggered videos.

#### Parts
The Raspberry Pi setup with camera connected
Daddy’s computer.

#### How to
Start up the Raspberry Pi if it is turned off and connect to it using VNC.
Open a terminal and enter the following commands one at a time (an explanation of each command is given below):
cd /home/pi
		git clone https://github.com/billw2/pikrellcam.git

		cd pikrellcam

		./install-pikrellcam.sh
The first command changes directory (cd) to the folder /home/pi. You might not see anything happen for this one.
The second command downloads (or clones) the software into the /home/pi folder. This one should provide some text about cloning on the terminal.
The third commend changes directory into the new pikrellcam folder. You will see the blue ‘~/pikrellcam’ appear before the $ prompt.
The fourth command runs a script (ending in .sh) to install the software on the Raspberry Pi. You will be asked some questions.
At the first question just hit ‘Return’ to use the default port number 80.
At the second question type ‘yes’ and hit ‘Return’ again. This will ensure that the camera starts every time we turn on the Raspberry Pi.
At the third question just hit ‘Return’ again to leave the password blank.
 The pickrellcam software will now install for a few minutes. Another drink?
It should end with an ‘Install finished’ message.
Enter the following command at the terminal and press ‘Return’. It tells you what address the Raspberry Pi has on the network. It should be four numbers separated by full stops and starting with something like 192. Remember the numbers.
hostname -I
Open a browser window – click on the globe icon at the top of the screen.
In the browser address type the numbers and full stops exactly as you see them in the terminal window.
The pikrellcam software OSD (On Screen Display) should be displayed. You may have to click on ‘System’ and ‘Start’ to get a picture up and stop the window jerking about.
If you’ve done it all correctly you should she a live picture from the camera.

### 7. Test the video recording and add some extra storage.

#### Parts
The Raspberry Pi setup with camera connected
Daddy’s computer.
A USB memory stick.

#### How to
Still using VNC to control the Raspberry Pi and with the pikrellcam software running, find and click the ‘Enable: Motion’ button on the OSD. The display in the live picture should turn from saying ‘Motion OFF’ in the bottom left hand corner to ‘Motion ON’.
Try moving something in front of the camera and trigger a movie. You have to stop moving in front of the camera to stop it recording after a few seconds.
Click on the ‘Media: Videos’ button and you should see your video recorded and you can play it back again. It will be a bit fuzzy and jerky because it is running on the Raspberry Pi and we’re looking at it remotely. Later we will learn how to transfer the video onto Daddy’s computer and watch it very clearly and smoothly.
On the saved video screen you will see it tells you how much free space you have to store videos and how much is left as a percentage of the total space. We need to increase the space available by adding a USB memory stick to the system. This will also stop the Raspberry Pi operating system micro USB card from wearing out with all the videos being written and deleted all the time.
First we have to format the blank USB stick. Minimise the VNC window so you can see your desktop on Daddy’s computer.
Plug in the USB memory stick to any USB port on Daddy’s computer.
The Nautilus file browser may start. You should see the stick in the list of the left called something like ‘31 GB Volume’.
Right click on the ‘31 GB Volume’ and select ‘Format...’. In the window that pops up select ‘Don’t overwrite existing data (Quick)’, and ‘Compatible with Linux systems (Ext4)’, and choose a name – something like ‘jimsvids’ ; easy and memorable. And click on ‘Format...’.
Read the security information on the next window and if you are happy click ‘Format’. One it has finished formatting the drive you can see it appear in the list with its new name – whatever you called it. Click on the upward pointing arrow to eject the drive. It should disappear and you might see a message on the screen saying it is now safe to remove it.
Remove the USB drive from the computer.
Swap back to the Raspberry Pi using VNC. Open a terminal and type:
ls -hal /dev | grep sd
This will list (ls -hal) everything in the ‘devices’ folder (/dev) and only display it if it contains anything with sd in the file name. The ‘grep’ does the matching. You should see nothing at the moment, just back to the $ prompt.
Plug the USB stick into a spare USB port on the Raspberry Pi. Any one will do.
You will probably see a window that has detected the new drive and asks you if you want to open it. Go ahead and you should see it mounted under something like /media/pi/<whatever-you-called-your-drive>. Close the window.
Go back to your terminal and type the same ‘ls’ command. (You can just hit up-arrow and enter as a speedier way of entering the same command.) This time you should see some output. Because the drive is labelled ‘sda’ our pattern ‘sd’ has matched and we get it displayed. Remember the ‘sda’ or whatever comes up.
We need to tell the pikrellcam software that the new USB drive is there and to save the videos to it. To do that we have to edit one of the set-up scripts. In the terminal type:
nano ~/pikrellcam/scripts/startup
‘nano’ is the Raspberry Pi’s text editor. It will open the file ‘startup’ located in /home/pi/pikrellcam/scripts. (The ~ is short for /home/pi.)
In the nano editor find the line MOUNT_DISK=””. (The line without the # before it.) Delete the “” and replace it with sda1 if your USB drive appeared as ‘sda’ before.
Save the file by hitting Ctrl-X, answer ‘y’ when asked if you want to overwrite the file and hit Enter. You should exit the nano editor and be returned to the $ prompt.
Go back to the pikrellcam OSD. Click on the PiKrellCam:raspberrypi at the top of the OSD. Click on the System block and then click on Stop. Wait for the OSD to display ‘PiKrellCam Stopped’. Then click on Start. When pikrellcam has started again click back to the Media: Videos screen. There should be no recorded videos yet and the amount of free memory should display as something like 30 GB.
Test the system by recording another video and playing it back. Don’t forget to enable the motion detection.

### 8. Configure pikrellcam software to correct some settings and make it email you every time it takes a video.

#### Parts
The Raspberry Pi setup with camera connected, and memory stick.
Daddy’s computer.

#### How to
First update your package list and then install some software to help the Raspberry Pi send you an email. In a terminal enter each of the following commands and press Enter after each one:
sudo apt-get update
sudo apt-get install ssmtp mailutils
Answer ‘y’ to any questions about disk space.
When it’s finished you should be able to check they have installed OK by typing the following commands in turn. You have to hit ‘q’ to quit after each one. They just show the manual pages for each command:
man ssmtp
man mailutils
Next we have to edit the ‘ssmtp.conf’ configuration file to tell it our email details. We have to have a gmail account that the Raspberry Pi can send emails to which will relay them to us. The email for that account (which Daddy already created) is r Enter:
sudo nano /etc/ssmtp/ssmtp.conf
Change the ‘root=postmaster’ to ‘root=sc’
Change the ‘mailhub=...’ to ‘mailhub=smtp.gmail.com:587’
Delete the ‘#’ in front of ‘FromLineOverride=YES’
Add ‘AuthUser=gmail.com’
Add ‘AuthPass=’
Add ‘UseSTARTTLS=YES’
Get Daddy to check your entries before hitting Ctrl-X to write the changes and exit.
Enter the following command to send a test message.
Echo “Testing...” | mail -s “Test Message” om 
Log in to your email and see if you get an email – it might take a few seconds to come through.
Now we have to edit the ‘pikrellcam.conf’ configuration file:
sudo nano ~/.pikrellcam/pikrellcam.conf
First use the ‘Page Down’ key to get right to the end of the file. Here we change one camera setting. When we build the whole camera we will find out that the picture is upside down. We can rotate it the right way up by editing the ‘rotation 0’ line to read ‘rotation 180’.
Go a bit further up in the file and in the ‘Miscellaneous Options’ section we have to change the latitude and longitude settings to be where we live. This way if we want (later) to set the camera to be off at night it will know when the sunrise and sunset is.
latitude N
longitude W
Finally much further up find the ‘on_motion_preview_save’ option. Set it to be
on_motion_preview_save mpack -s pikrellcam@$H $F 
Hit Ctrl+X and confirm the writing of the file.
Now stop and restart the pikrellcam from the OSD. Trigger a video by waving at the camera. Wait until it finishes recording and then see if you get an email with a picture of your hand!

### Set up archiving of the videos from the Raspberry Pi to another computer

#### Parts
* The Raspberry Pi setup with camera and memory stick connected
* Another computer (*dadcomp*)

#### How to
* SETUP REMOTE ARCHIVE STUFF!

* Find out the URL for the *dadcomp* computer; open a terminal on the *dadcomp* and type:
```
	hostname -I
```
* Make a note of the numbers displayed.
* Change the the Raspberry Pi using the VNC connection.
* Edit the *hosts* file on the Raspberry Pi to give the *dadcomp* computer a nickname on the Raspberry Pi. Open a terminal and type:
```
	sudo nano /etc/hosts
```
* Add a line to the file at the end, where the a, b, c, and d are the numbers you wrote down.
```
	dadcomp		a.b.c.d
```
* Hit Ctrl+X when you are finished and type ‘y’, and Enter, to save the file.
* Edit the *fstab* file; enter in the terminal:
```
	sudo nano /etc/fstab
```
* Add this single line to the end of the file and save it in the usual way (Ctrl+X, y, Enter)
```
	dadcomp:<FULL_PATH_TO_ARCHIVE_ON_DADCOMP> /home/pi/pikrellcam/media/archive nfs users,noauto 0 0
```
* Mount the remote archive from the Raspberry Pi.
```
	sudo mount dadcomp:<FULL_PATH_TO_ARCHIVE_ON_DADCOMP>
```
* Nothing should happen if it’s all worked.
* Enter ```df``` in the terminal and hit enter; you should see a line in the output confirming the connection.
* Go back to the pikrellcam OSD and perform a stop/start sequence; you should now see an ‘NFS Archive’ button appear on the videos screen.
* Select a good video and press the button.
* On *dadcomp* look in the folder ```<FULL_PATH_TO_ARCHIVE_ON_DADCOMP>``` and click deeper into the folders to find the video you just archived.
* Double click on the video to play it; it should be nice a smooth.
* Now you are ready to build the camera hardware and see what we can catch! 


SCJK 4 July 2018
