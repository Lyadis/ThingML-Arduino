# ThingML-Arduino
Shorts tutorials to getting started with ThingML over Arduino Uno

##Summary
###1 Basics
####1.1 Hello World on the serial port
####1.2 LED (Digital Output)
####1.2 Timer
####1.4 Simple Button (Digital Input)
####1.5 Sensor (Analogic Input)

###2 Library
####2.1 AdafruitLCD RGB Shield
####2.2 Your own

###lib

##ArduinoMsgs
Most arduino specific feature will be used via messeges over the arduino port of ArduinoApp.

###Time relative message
####receives 
*4ms_interrupt
*100ms_interrupt
*1s_poll
*timeout(id : UInt8)

####sends 
*timer_start(id : UInt8, time: Integer)
*timer_cancel(id : UInt8)

###Serial port relative message
####sends 
*serial_print_str(msg: String)
*serial_print_dec(num: Double)
*serial_print_num(num: Integer)
####receives 
*serial_rx_char(c : Char)

###Pin relative message
####sends 
*setDigitalHigh(pin : UInt8)
*setDigitalLow(pin : UInt8)
*setOutput(pin : UInt8)
*setInput(pin : UInt8)
*readDigital(pin : UInt8)
*readAnalog(pin : UInt8)

####receives 
*readDigitalResponse(DigitalState : DigitalState)
*readAnalogResponse(res : Int16)
