# WSL

Step 1: enable developer mode in Windows 10

Enable developer mode (and restart) and Windows Subsystem for Linux (restart again) following:
https://superuser.com/questions/1217167/cant-find-windows-subsystem-for-linux-feature-to-install-bash-for-windows/1217176

** according to Microsoft, recent Windows 10 builds shouldn’t require this step, but mine did

Step 2: get and install Ubuntu

Download Ubuntu from Windows Store and install.

Notes:
-	Local drives are accessed as mounted drives.  To get to the c drive: `cd /mnt/c/`
-	To mount new drive: to mount RIO (samba drive) as r:
```
sudo mkdir /mnt/r
sudo mount -t drvfs '\\PATH’ /mnt/r
```
(PATH = path to samba share)
-	more info here: https://blogs.windows.com/buildingapps/2016/07/22/fun-with-the-windows-subsystem-for-linux/#b9CC5IfEL1Gw8f2J.97

Step 3: get and install Xming

a)	Download Xming and install

b)	Configure following:
https://www.pcgamer.com/linux-in-windows-10/

notes:
-	Launch Xming before WSL
-	To launch desktop from WLS:
	`dbuslaunch --exit-with-session ~/.xsession`

Step 4: get and install Matlab:

see this for more info: https://www.mathworks.com/matlabcentral/answers/308911-can-i-install-matlab-in-bash-on-ubuntu-on-windows#answer_333214

a)	install Matlab for Linux

b)	configure to make work in WSL:
```
sudo apt install execstack
sudo apt install default-jre 
cd /usr/local/MATLAB/R2018b/bin
sudo execstack -c glnxa64/libmwblas.so
sudo execstack -c glnxa64/libmwlapack.so
sudo execstack -s glnxa64/MATLAB
```
Step 5: install ISCE and StaMPS
