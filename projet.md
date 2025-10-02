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
from microbit import * <br>
import radio <br>

message = radio.receive("lumiere")

radio.on()

radio.config(channel = 10, power = 3, length = 32, group=10)

while True: <br>
  if message: <br>
    pin0.write_digital(1) <br>
    sleep(5000) <br>
    pin0.write_digital(0) <br>
    sleep(5000) <br>
