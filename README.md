ShereCar RC Car Controller
====================

Control a RC car over the internet via node.js using socket.io and johnny-five.

Hardware Requirements
----------------------
* Raspberry Pi
* Arduino UNO
* USB connection from RPi to Arduino UNO
* Wires for power and ground
* Wires from Aruidno Pin 10 to steering servo
* Wires from Aruidno Pin 9 to throttle servo

Libraries Requirements
---------------------
* Socket.io
* Express.js
* Johnny-five
* OpenCV
* RaspiCam
* Python OpenCV
* Python PiCamera

Getting the Raspberry Pi Ready
------------------------------
* Update/upgrade OS, then restart
 * sudo apt-get update
 * sudo apt-get upgrade
 * sudo rpi-update
 * sudo ldconfig
 * sudo shutdown -r now
* Note: If rpi-update doesn't work, certificates may be needed, there are notes on how to do this at the bottom
* Install node.js
 * wget http://node-arm.herokuapp.com/node_latest_armhf.deb
 * sudo dpkg -i node_latest_armhf.deb
* Install node modules
 * npm install socket.io express johnny-five

To run opencv.py
* Install python libraries
 * sudo apt-get install libopencv-dev python-pip python-opencv python-dev python-picamera

Using the Controller
-------------------
* Start up the nodejs server
 * sudo node server.js
* Open a web browser to the Raspberry Pi's internet location
* Enter the Raspberry Pi's address into the field and click the connect button
* Control the RC Car

Alternate options to run
* Run the node server when there's no Arduino attached
 * sudo node server.js noArduino
 
File Layout
-----------
* server.js - socketio server, forwards information between opencv.py and webpage. Commands Arduino via johnny-five
* index.html - webpage served by node server
 * manual control socketio emits
 * robot status from socketio
 * retrieves static elements from public folder
* opencv.py - raspberry pi camera and opencv processing
 * only has face detection for now
 * updates opencv image in public folder

Possible Future Enhancements
-----------------------------
* Nodejs version for opencv and raspi camera
* Proper 3d printed mounts for RC car components
* Easier way to configure RC car for use at new locations
* Stream OpenCV video to the internet

Possible Future Library Requirements
-----------------------------------
* ZeroRPC - and ZMQ
 * sudo apt-get install libzmq-dev
 * npm install zerorpc
 * sudo pip install zerorpc

Other Information
-----------------
* If rpi-update doesn't work, git and/or certifications may be needed, use Hexxeh
 * $ sudo apt-get install ca-certificates
 * $ sudo apt-get install git-core
 * $ sudo apt-get install rpi-update
* Then use rpi-update as normal
 * $ sudo rpi-update
 * $ sudo ldconfig
 * $ sudo reboot
