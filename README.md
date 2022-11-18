# Circuitpython-8-rpi-pico-OVERCLOCK
Modified circuitpython 8 build for raspberry pi pico. Allows to change processor clock speed by microcontroller module.

```
import microcontroller

print(microcontroller.cpus[0].frequency)      # 125 000 000 Hz in default
microcontroller.cpus[0].frequency = 150000    #set clock speed to 150mHz
print(microcontroller.cpus[0].frequency)      # 150 000 000 Hz
```

This is how You can set cpu clock frequency using added functionality. Normally frequency is read only on pico, so this will fail on normal build, but  modified one work correctly. However You must notice two things:
1. Frequency is printed in Hz and seted in kHz!!!
2. This code set speed of both pico cores! Under this set instruction, there is hidden call of set_sys_clock_khz from pico sdk, that set speed of whole processor!

As You see, this modification is very dirty, but it works. For example, I use it in my mp3 player project. Default speed of pico processor is not enought to play high-qulity music, but after overclocking, it plays flawlessly.

Enjoy!
