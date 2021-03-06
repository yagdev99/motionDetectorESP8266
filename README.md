# IoT based Intruder Alarm using ESP8266


## For this project the following will be required:

  * #### ESP8266 (ESP-12E) Board 
This has been selected as the controller for this system due to its compact size, ease of use, and compatibility with Arduino IDE. ESP8266 is an open-source Wi-Fi-enabled module. It is integrated with TCP/IP protocol stack that can give any microcontroller access to your Wi-Fi network. The ESP8266 is capable of either hosting an application or offloading all Wi-Fi networking functions from another application processor. ESP8266 contains 8 digital i/o pins and one analog i/o pin.
  
  * #### PIR Motion Sensor (HR SC501) 
A passive infrared sensor (PIR sensor) is an electronic sensor that measures infrared radiation in its field of view from objects. PIR sensors sense general movement, but don’t have information on who moved or what. These sensors allow you to sense motion, generally used to detect whether a human has moved in or out of the sensor range. They are small, inexpensive, low-power, easy to use and don’t wear out.

| Pin or Control      | Function |
| ----------- | ----------- |
| Time Delay Adjust      | Sets how long the output remains high after detecting motion.... Anywhere from 3 seconds to 5 minutes.|
| Sensitivity Adjust   | Sets the detection range.... from 3 meters to 7 meters   |
|Trigger Selection Jumper|Set for single or repeatable triggers.|
|Ground pin|Ground input|
|Output Pin|Low when no motion is detected.. High when motion is detected. High is 3.3V|
|Power Pin|5 to 20 VDC Supply input|


  * #### Buzzer(One we have used in this project is LOW-LEVEL TRIGGER i.e. will be triggered when the input is LOW) 
Here we have used an active buzzer to make a sound after motion detected. The active buzzer has an internal oscillating source, the buzzer will sound as soon as it is energized.
 

| Pin or Control      | Function |
| ----------- | ----------- |
|Ground pin|Ground input|
|Input Pin|When Input is LOW, the buzzer is turned On. When input it is HIGH the buzzer does not sound*|
|Power Pin|3.3 to 5 VDC Supply input|

* *We have used a low trigger buzzer 

  
  * #### Jumper Wires 
Jumper wires are simply wires that have connector pins at each end, allowing them to be used to connect without soldering. Jumper wires are typically used with breadboards and other prototyping tools to make it easy to change a circuit as needed.
  
  * #### LED 
A light-emitting diode (LED) is a semiconductor device that emits visible light when an electric current passes through it.
  
  * #### Breadboard 
A breadboard is a platform you can use to build and test electronic circuits, usually without having to do any soldering. Certain parts of the breadboard are wired together so that electricity can flow from component to component in orderly rows. Breadboards are useful for quickly testing and prototyping electronics ideas.
Also, Breadboard can be used without soldering, which makes it easy to remove components and reuse them after experimenting.


## Working Theory
*	We have connected the PIR motion sensor to the digital pin D8 (GPIO 15) of NodeMCU.
*	Whenever the PIR detects motion then the output state of the PIR sensor will change which will be detected by the controller.
*	We have programmed the NodeMCU to make an HTTP GET request to our IFTTT Webhooks app.
*	Whenever the HTTP GET request has been made then it will trigger a notification alert on our mobile phone or the device connected.

## Circuit and Connection

![Schematic](https://github.com/yagdev99/motionDetectorESP8266/blob/master/Resources/11.jpg)

## IFTTT Applet Creation 
 * Download the Andriod app from Play Store
 * Create an Account (If you don't have an account)
 
 1. Click on your profile icon and select the create option
 
 2. Now click on +This
 
 3. Search for "Webhooks" and select it
 
 4. Choose trigger option, "Receive a Web Request"
 
 5. Give a name to your event. In our case, we have used "motion_detected"
 
 6. Now click on +That
 
 7. Now from “choose action service”,
   
 8. Search for notification in the search box and click on the notification icon. \
    • Note that you must be installed and logged in to the IFTTT app on your phone for the notifications to work.
    
 9. Choose Simple Notification
 
 10. Type the custom message you want to receive the notification.
 
 11. Click Finish.
 
 #### Obtaining the HTTP GET request URL
 
 1. Log in to your IFTT account
 
 2. Click on profile and choose "My Services"
 
 3. Select Webhooks
 
 4. Click on Documentation
 
 5. Now replace "{event}" with your even name in Step 5 of IFTTT Applet creation
 
 6. Now copy the key and paste it into the code
 
 
 ## Basic flow of the program
 
 ![flow](https://github.com/yagdev99/motionDetectorESP8266/blob/master/Resources/23.png)
