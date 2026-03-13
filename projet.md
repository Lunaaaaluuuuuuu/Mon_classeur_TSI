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


radio.config(channel = 10, power = 3, length = 32, group=10)
if radio.receive("nuit"):
  recul(500, 500)
if radio.receive("jour"):
  avance(500, 500)
avance(None, None)

while True:
  pass
  retestfrom microbit import *
import radio 

radio.config(channel = 10, power = 3, length = 32, group=10)

radio.on()

if radio.on():
    display.show(Image.YES)
    


while True :
    pin1.read_analog()
    if pin1.read_analog() <= 100:
        radio.send('nuit')
        sleep(5000)
    elif pin1.read_analog() >= 100:
        radio.send('jour')
        sleep(5000)
    else :
        sleep(5000)
        
    
