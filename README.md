# IoT based Home Automation and Security


[![SaiLikhith](https://img.shields.io/badge/Sai%20Likhith-Repository-brightgreen)](https://github.com/SaiLikhith7/)


This is an embedded systems based Arduino project which takes care of security and home appliances operations using the android mobile or sms. With the Arduino uno and Windows 10, we can build a home automation system that is capable of operating home devices automatically.
Mobile phone is a revolutionary invention of the century. It was primarily designed for making and receiving calls & text messages, but it has become the whole world after the Smart phone comes into the picture. In this project we are building a home automation system, where one can control the home appliances, using the simple GSM based phone, just by sending SMS through his phone. In this project, no Smart phone is needed, just the old GSM phone will work to switch ON and OFF any home electronic appliances, from anywhere. You can also check some more Wireless Home Automation projects here: IR Remote Controlled Home Automation using Arduino, Bluetooth Controlled Home Automation along with DTMF Based Home Automation, PC Controlled Home Automation using Arduino.


Working Explanation
In this project, Arduino is used for controlling whole the process. Here we have used GSM wireless communication for controlling home appliances. We send some commands like “#A.light on*”, “#A.light off*” and so on for controlling AC home appliances. After receiving given commands by Arduino through GSM, Arduino send signal to relays, to switch ON or OFF  the home appliances using a relay driver.

Circuit Components:

- Arduino UNO
- GSM Module
- ULN2003
- Relay 5 volt
- Bulb with holder
- Connecting wires
- Bread board
- 16x2 LCD
- Power supply
- Cell phone


Here we have used a prefix in command string that is “#A.”. This prefix is used to identify that the main command is coming next to it and * at the end of string indicates that message has been ended.

When we send SMS to GSM module by Mobile, then GSM receives that SMS and sends it to Arduino. Now Arduino reads this SMS and extract main command from the received string and stores in a variable. After this, Arduino compare this string with predefined string. If match occurred then Arduino sends signal to relay via relay driver for turning ON and OFF the home appliances. And relative result also prints on 16x2 LCD by using appropriate commands.

Here in this project we have used 3 zero watt bulb for demonstration which indicates Fan, Light and TV.

Below is the list of messages which we send via SMS, to turn On and Off the Fan, Light and TV:


|S.no.|Message|Operation|
|-----|-------|---------|
|1|#A.fan on*|Fan ON|
|2|#A.fan off*|Fan OFF|
|3|#A.light on*|Light ON|
|4|#A.light off*|Light OFF|
|5|#A.tv on*|TV ON|
|6|#A.tv off*|TV Off|
|7|#A.all on*|All ON|
|8|#A.all off*|All OFF|

 
GSM Module:

GSM module is used in many communication devices which are based on GSM (Global System for Mobile Communications) technology. It is used to interact with GSM network using a computer. GSM module only understands AT commands, and can respond accordingly. The most basic command is “AT”, if GSM respond OK then it is working good otherwise it respond with “ERROR”. There are various AT commands like ATA for answer a call, ATD to dial a call, AT+CMGR to read the message, AT+CMGS to send the sms etc. AT commands should be followed by Carriage return i.e. \r (0D in hex), like “AT+CMGS\r”. We can use GSM module using these commands:

ATE0 - For echo off

AT+CNMI=2,2,0,0,0  <ENTER>          - Auto opened message Receiving.  (No need to open message)

ATD<Mobile Number>; <ENTER>    -  making a call (ATD+919610126059;\r\n)

AT+CMGF=1 <ENTER>                       - Selecting Text mode

AT+CMGS=”Mobile Number” <ENTER> - Assigning recipient’s mobile number

>>Now we can write our message

>>After writing message

Ctrl+Z  send message command (26 in decimal).

ENTER=0x0d in HEX


The SIM900 is a complete Quad-band GSM/GPRS Module which delivers GSM/GPRS 850/900/1800/1900MHz performance for voice, SMS and Data with low power consumption.

Circuit Description
Connections of this GSM based home automation circuit are quite simple, here a liquid crystal display is used for displaying status of home appliances which is directly connected to arduino in 4-bit mode. Data pins of LCD namely RS, EN, D4, D5, D6, D7 are connected to arduino digital pin number 6, 7, 8, 9, 10, 11. And Rx and Tx pin of GSM module is directly connected at Tx and Rx pin of Arduino respectively. And GSM module is powered by using a 12 volt adaptor. 5 volt SPDT 3 relays are used for controlling LIGHT, FAN and TV. And relays are connected to arduino pin number 3, 4 and 5 through relay driver ULN2003 for controlling LIGHT, FAN and TV respectively.


