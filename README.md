# ThingML-Arduino
Shorts tutorials to getting started with ThingML over Arduino Uno

##Summary
###1 Basics
####1.1 Hello World on the serial port
####1.2 LED (Digital Output)
####1.3 Timer
####1.4 Simple Button (Digital Input)
####1.5 Sensor (Analogic Input)

###2 Library
####2.1 AdafruitLCD RGB Shield
####2.2 Your own

###lib

## Architecture

![Simple configuration](https://github.com/Lyadis/ThingML-Arduino/blob/master/img/basic.png?raw=true)

With this arduino abstraction layer (_Arduino.thingml) you typically developp in this configuration. Your Application sends instruction to the Arduino Abstraction Layer via the arduino port, and collect result the same way.

![with a lib](https://github.com/Lyadis/ThingML-Arduino/blob/master/img/app-ardu-lcd.png?raw=true)

You can developp or use other library or other abstraction layer for some other hardware (like a shield) and use it this way. Be carefull though, messages in this configuration are broadcast to all things plugged to the port. (in the case of readDigitalResponse or readAnalogResponse, the id parameter will help you to filter and ract only to messages you're supposed to, (use `guard`) (This is true only because the arduino port is in synchrone mod.)

## A problem you might encounter (and its solution)

![execution order](https://github.com/Lyadis/ThingML-Arduino/blob/master/img/3things.png?raw=true)

##ArduinoMsgs
Most arduino specific feature will be used via messeges over the arduino port of ArduinoApp. 
Here is the list seen from your arduino app.

###Time relative message
####received 
* 4ms_interrupt
* 100ms_interrupt
* 1s_poll
* timeout(id : UInt8)

####sent 
* timer_start(id : UInt8, time: Integer)
* timer_cancel(id : UInt8)

###Serial port relative message
####sent 
* serial_print_str(msg: String)
* serial_print_dec(num: Double)
* serial_print_num(num: Integer)

###Pin relative message
####sent 
* setDigitalHigh(pin : UInt8)
* setDigitalLow(pin : UInt8)
* setOutput(pin : UInt8)
* setInput(pin : UInt8)
* readDigital(pin : UInt8)
* readAnalog(pin : UInt8)

####received 
* readDigitalResponse(pin : UInt8, DigitalState : DigitalState)
* readAnalogResponse(pin : UInt8, res : Int16)
