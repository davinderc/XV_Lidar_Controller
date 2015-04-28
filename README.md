XV Lidar Controller
===================

Control the Neato XV Lidar with an Arduino compatible board.  This has been forked from https://github.com/getSurreal/XV_Lidar_Controller and has been modified to use the Sparkfun Pro Micro and an external H-Bridge 
Used as an interface board to connect directly to the Neato XV Lidar and control the rotation speed through Pulse Width Modulation (PWM).

Copyright 2014 James LeRoy getSurreal.com
v1.3.0 - 2014/04/28 seaton@strobotics.com.au (Stephen Eaton) Ported to Pro Micro + external Motor Driver
v1.2.2 - Updated 2015/02/23
* http://www.getsurreal.com/products/xv-lidar-controller
* https://github.com/getSurreal/XV_Lidar_Controller

Based on the following work: 
* Nicolas "Xevel" Saugnier https://github.com/bombilee/NXV11/
* Cheng-Lung Lee https://github.com/bombilee/NXV11/tree/master/ArduinoMegaAdapter


##Description
The XV Lidar Controller receives the serial data from the XV Lidar looking for the RPM data embedded in the stream and uses a PID controller to regulate the speed to 300RPMs.  The data received from the Lidar is relayed to the USB connection for some upstream host device (PC, BeagleBone, Raspberry Pi) to process the data.

##Requirements

###Hardware
* Neato XV Lidar - Available on eBay
* Sparkfun Pro Micro https://www.sparkfun.com/products/12640
*  L9110 H-Bridge Board by http://www.dx.com/p/l9110-dual-channel-h-bridge-motor-driver-module-for-arduino-black-157149#.VT8B38622NU) or any external MOSFet board Connected to Pin 5 of Sparkfun Pro Micro.
* Firmware https://github.com/madeinoz67/XV_Lidar_Controller


###Software to build from source
* Arduino IDE (v1.0.6 tested. Newer or older may work)
* promicro - Software add-on to run Arduino sketches on the ProMicro (v1.19 tested. Newer or older may work)
 https://github.com/sparkfun/SF32u4_boards/archive/master.zip
* Copy the included libraries to the Arduino libraries directory

##Usage
Connect to the Pro Micro USB port at 115200 baud.  When sending commands use the newline character to signify the end of a command.

##Commands
Commands are case sensitive.
* Help - Show the list of commands available
* ShowConfig    - Show the running configuration
* SaveConfig    - Save the running configuration to EEPROM
* ResetConfig   - Restore the original configuration
* SetRPM        - Set the desired rotation speed (min: 200, max: 300)
* SetKp         - Set the proportional gain
* SetKi         - Set the integral gain
* SetKd         - Set the derivative gain
* SetSampleTime - Set the frequency the PID is calculated (ms)
* ShowRPM       - Show the rotation speed
* HideRPM       - Hide the rotation speed
* ShowDist      - Show the distance data
* HideDist      - Hide the distance data
* ShowAngle     - Show distance data for a specific angle (0 - 359 or 360 for all)
* MotorOff      - Stop spinning the lidar
* MotorOn       - Enable spinning of the lidar
* HideRaw       - Stop outputting the raw data from the lidar
* ShowRaw       - Enable the output of the raw lidar data

