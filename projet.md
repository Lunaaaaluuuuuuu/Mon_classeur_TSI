# To Do list pour le project de la fête de la science 2025
## **code radio BBC fete de la science**<br>
### **bbc numéro B :**<br>
from microbit import * <br>
import radio <br>
import music <br>

radio.on()

#radio = radio.on()


radio.config(channel = 10, power = 3, length = 32, group=10)

sleep(1000)

#if radio :
  #music.play(music.BLUES)
  

radio.send("lumiere")
radio.off()

### **bbc numéro A :**<br>
from microbit import *
import radio

def avance(vitesse, duree):
  pin0.write_analog(vitesse)
  pin8.write_digital(0)
  pin1.write_analog(vitesse)
  pin12.write_digital(0)
  sleep(duree)

def recul(vitesse, duree):
  pin0.write_analog(1023 - vitesse)
  pin8.write_digital(0)
  pin1.write_analog(1023 - vitesse)
  pin12.write_digital(0)
  sleep(duree)

message = radio.receive('lumiere')
radio.config(channel = 10, power = 3, length = 32, group=10)
if message:
  pass
avance(None, None)

while True:
  pass
