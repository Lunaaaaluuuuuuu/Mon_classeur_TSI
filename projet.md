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
  retest

  from microbit import *
import radio 

radio.config(channel = 10, power = 3, length = 32, group=10)

radio.on()

if radio.on():
    display.show(Image.YES)

def jour():
    pin1.write_analog(150 >= 1053)

def nuit():
    pin1.write_analog(0 < 149)

while True :
    pin1.read_analog()
    if jour():
        radio.send('ouvre')
        while jour():
            sleep(5000)
            pin1.read_analog()
            if nuit():
                break
   
    elif nuit():
        radio.send('ferme')
        while nuit():
            sleep(5000)
            pin1.read_analog()
            if nuit():
                break
