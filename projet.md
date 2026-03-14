from microbit import *
import radio

def avance(v, duree):
    pin8.write_digital(1)  # direction M1
    pin12.write_digital(0) # direction M2
    pin1.write_analog(v) # vitesse M1
    pin2.write_analog(v) # vitesse M2
    sleep(duree)

def recule(v, duree):
    pin8.write_digital(0)  # direction M1
    pin12.write_digital(1) # direction M2
    pin1.write_analog(v) # vitesse M1
    pin2.write_analog(v) # vitesse M2
    sleep(duree)
while True :
    display.show(Image.HAPPY)
    radio.config(channel = 10, power = 3, length = 32, group=10)
    message = radio.receive()
    print(message)
    if message == 'nuit':
        display.show(Image.NO)
        avance(800, 500)
        avance(0, 500)
        sleep(5000)
    elif message == 'jour':
        display.show(Image.YES)
        recule(800, 500)
        recule(0, 500)
        sleep(5000)

        
  retest
  
 from microbit import *
import radio 

radio.on()
radio.config(channel = 10, power = 3, length = 32, group=10)

while True :
    pin1.read_analog()
    if pin1.read_analog() <= 100:
        print(pin1.read_analog())
        radio.send('nuit')
        sleep(5000)
        while pin1.read_analog() <= 100:
            sleep(500)
    elif pin1.read_analog() > 100:
        print(pin1.read_analog())
        radio.send('jour')
        sleep(5000)
        while pin1.read_analog() > 100:
            sleep(500)
    else :
        sleep(5000)
        
    
