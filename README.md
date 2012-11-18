Printerface is something I cooked up to allow me printing to my 3d printers (reprap's) with the browser.
You connect a Raspberry pi to your printer and then this allows your printer to be autonomous and easily manageable from within any browser.
Little video explaining the usage is on youtube:
http://youtu.be/tsMdusrO6bk

```
# install prconsole
cd /home/pi
sudo apt-get install python-serial python-wxgtk2.8 python-pyglet
wget https://github.com/kliment/Printrun/tarball/master -O pronterface_src.tar.gz
tar -xzvf pronterface_src.tar.gz
mv kliment-Printrun-* printrun
mkdir /hom/pi/printrun/

# install node.js and npm
cd /home/pi
sudo apt-get install nodejs npm git

# get printerface
cd /home/pi
git clone git://github.com/w-A-L-L-e/printerface.git
mkdir /home/pi/printerface/gcode_uploads

# forever keeps our printerface running even if it crashes, and creates a logfile while we're at it...
sudo npm install -g forever@0.9.2

# now actually fire it up, put this line in /etc/rc.local to have it on boot
cd /home/pi/printerface && forever start printerface.js
```

Once started, you can access the web interface at http://<IP>:8080/