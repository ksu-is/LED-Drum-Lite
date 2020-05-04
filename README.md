# LED-Drum-Lite

import RPi.GPIO as GPIO
import time
GPIO.setmode(GPIO.BOARD)
GPIO.setup(8,GPIO.OUT)
GPIO.setup(11,GPIO.OUT)
GPIO.setup(13,GPIO.OUT)

# turn off Defaul 3.3V  LED
GPIO.output(8,False)
GPIO.output(11,False)
GPIO.output(13,False)

color_list = ["red", "yellow", "green", "teal", "blue", "purple", "white", "party", "off"]



while True:
    
    color = input ("Enter a color: ")
    if color == "exit":
        break
    elif color in color_list:
        color_list_index = color_list.index(color)
        

        #RED
        if color_list_index == 0:
            GPIO.output(8,True)
            GPIO.output(11,False)
            GPIO.output(13,False)
        #YELLOW
        elif color_list_index == 1:
            GPIO.output(8,True)
            GPIO.output(11,True)
            GPIO.output(13,False)

        #GREEN
        elif color_list_index == 2:
            GPIO.output(8,False)
            GPIO.output(11,True)
            GPIO.output(13,False)
        #TEAL
        elif color_list_index == 3:
            GPIO.output(8,False)
            GPIO.output(11,True)
            GPIO.output(13,True)

        #BLUE
        elif color_list_index == 4:
            GPIO.output(8,False)
            GPIO.output(11,False)
            GPIO.output(13,True)

        #PURPLE
        elif color_list_index == 5:
            GPIO.output(8,True)
            GPIO.output(11,False)
            GPIO.output(13,True)

        #WHITE
        elif color_list_index == 6:
            GPIO.output(13,True)
            GPIO.output(8,True)
            GPIO.output(11,True)

        #PARTY
        elif color_list_index == 7:
            for x in range (0,10):
                GPIO.output(8,True)
                time.sleep(.1)
                GPIO.output(11,True)
                time.sleep(.1)
                GPIO.output(8,False)
                time.sleep(.1)
                GPIO.output(13,True)
                time.sleep(.1)
                GPIO.output(11,False)
                time.sleep(.1)
                GPIO.output(8,True)
                time.sleep(.1)
                GPIO.output(13,False)
                GPIO.output(8,False)
                
        #OFF
        elif color_list_index == 8:
            GPIO.output(13,False)
            GPIO.output(8,False)
            GPIO.output(11,False)
    else:
        print("Try a different color!")
    
x = input("Press enter to confirm.")
GPIO.cleanup()
