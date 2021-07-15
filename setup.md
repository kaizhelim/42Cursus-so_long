# Setup

## Windowing System
The X Window System is a windowing system for bitmap displays, common on Unix-like operating systems. 
X provides the basic framework for a GUI environment: drawing and moving windows on the display device and interacting with a mouse and keyboard. 
- X does not mandate the user interface – this is handled by individual programs. 
- As such, the visual styling of X-based environments varies greatly; different programs may present radically different interfaces.

## Installing and Running Windows X Server
There are many X Servers running on Windows, but VcXsrv is easy to use.\
In the old days, there was only Cygwin and it was difficult to use.

1. VcXsrv Windows X Server: [Download here](https://sourceforge.net/projects/vcxsrv/)

<img src="https://user-images.githubusercontent.com/76621210/125737342-4982d795-9e06-4dfb-9258-1a179f89383c.png" height="200"/>

2. Launch it and specify the installation options and installation destinations.

<img src="https://user-images.githubusercontent.com/76621210/125737617-44aa4414-dfb3-4c6a-813f-d851b57391c9.png" height="200"/>

3. Leave everything else as default

<img src="https://user-images.githubusercontent.com/76621210/125737883-64d33f11-272d-49d0-979b-17709f73c208.png" height="200"/>
<img src="https://user-images.githubusercontent.com/76621210/125737901-2173f1b4-6280-43b9-8a05-02534c549cb8.png" height="200"/>

4. Run XLaunch

<img src="https://user-images.githubusercontent.com/76621210/125738725-5ac7c1a1-7b81-4993-b00c-b49d5bc71795.png" height="50"/>

5. Configure the VcXsrv initial setting, boot and launch option. Select Multiple Windows (default) as display settings. You can change it later.

<img src="https://user-images.githubusercontent.com/76621210/125739372-9dbde2ef-f29e-42ee-8621-b3770da6a9ce.png" height="300"/>

6. Leave it as default.

<img src="https://user-images.githubusercontent.com/76621210/125739655-6db73970-5cc3-4d3f-afcb-6bbb980e4c79.png" height="300"/>

7. Check "Disable access control" to allow you to accept the X protocol from the outside. 
After accepting the X protocol from the outside, you can only display the GUI app remotely on your PC.
If you do not check the option now, you will need to setup "External permissions" later.

<img src="https://user-images.githubusercontent.com/76621210/125739840-cae288c3-4b29-465e-927e-606a0271b300.png" height="300"/>

8. Finish!!

<img src="https://user-images.githubusercontent.com/76621210/125740633-483bd3d8-002d-4c80-a8bd-74790c66b399.png" height="300"/>

## WSL and VcXsrv Additional Configuration (Optional)
By default, every time you launch the OS, you need to click the VcXsrv icon to launch the program. 
When you start VcXsrv, the wizard will start up and you will need to make the settings every time. 
It is not difficult but it might be troublesome to you every time. 
If you frequently use the x window, it is useful to include a setting that makes VcXsrv start automatically when you start the OS.

Guide: [Linux GUI application on windows: WSL2 and VcXsrv configuration](https://blog.nimamoh.net/wsl2-and-vcxsrv/)

## Install Required Packages
- sudo apt-get update
- sudo apt-get install x11-apps -y
- sudo apt-get install gcc make libbsd-dev libxext-dev xorg

## Setup Display Environment Variables on WSL and Export Display for XWindows  
- For WSL1: export DISPLAY=0:0
- For WSL2: export DISPLAY=$(grep -m 1 nameserver /etc/resolv.conf | awk '{print $2}'):0
<!-- echo 'export DISPLAY=$(grep -oP "(?<=nameserver ).+" /etc/resolv.conf):0' >> ~/.bashrc -->
<!-- source ~/.bashrc -->

## Testing 
Run the following command in the WSL terminal. An appication should pop out in a separate window.
- xeyes
- xclock
