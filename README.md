# mariposa-pcb

mariposa is the microcontroller board for the coquette keyboard. note that this project, this board, the associated keyboard shields, and all firmware, is untested and provided with no guarantees or liability for failures, safety hazards, reguatory compliance, and/or injuries and/or losses in any form.

## bill of materials

- Raytac MTBT53-1M nRF5340 module - this is the microcontroller that runs the keyboard
- TI TPS62842DGRR DCDC converter - chosen for its 60nA quiescent current, this powers it
- TI BQ25170DSGR lipoly charger - charges the battery
- Sharp memory-in-pixel LCD that fits on top and has the 10-pin connection that matches the pinout, a few sizes should work
- 2 TI LM66100DCK ideal diode ICs - used to implement ORing between the battery and USB
- 1 TI TPS22917DBV - high side load switch for addressable RGB power. the quiescent on those things is soooooo high relative to the keeb you'll probably want to turn off power completely on battery
- 1 TI SN74LV1T125DCK - converts addressable RGB logic to input voltage for LEDs
- 1 32.768KHz 9pF load cap 3215 2-pin SMD crystal - external LFXO to reduce power use compared to internal oscillator
- 1 TI TSD05C TVS diode, protects USB VBUS input from ESD events
- 4 TI TPD4E1U06 TVS diode arrays, protects exposed data pins + USB data lines from ESD events
- 1 390pF NP0 ceramic capacitor, used to set ARGB power switch slew rate
- 1 560pF NP0 ceramic capacitor, the sharp memory display wants it, idk why
- 3 10nF 0603 ceramic capacitors, two for USB power RC filter, one for battery voltage sampling
- 8 0.1uF 0603 ceramic capacitors, used for decoupling
- 9 1uF 0603 ceramic capacitors, used for decoupling
- 3 4.7uF 1206 ceramic capacitors, used for decoupling
- 2 10uF 0805 ceramic capacitors - decopling, but more power!
- 1 R2.2 0805 thick film resistor, VBUS input surge protection
- 1 0603 1% resistor for DCDC vset, 0R - 1.8V, 1.74k - 2.2V, 21.5k - 3V, 28.7k - 3.1V, 38.3k - 3.2V, 52.3k - 3.3V – use 52.3k if you want accessories that use power to work, but 2.2V is probably the most efficient if no screen, no add-ons, no display, and no UV underglow on גחלילית או פרפר 
- 1 0603 1% resistor for charger VSET, 27k for 4.2V, 36k for 4.1V which will prolong battery longevity at the expense of runtime but this thing should last ages anyway. up to you.
- 1 2xR27 2x0603 convex resistor array - impedance matching USB data pair
- 1 0603 1% resistor for charger ISET, formula is 300/resistor in kohm = charge current in mA. i'm using 1.8k for 167mA charge current. most batteries it is dangerous to exceed 1C (charge current in mA = battery capacity in mAh)
- 2 R620 0603 thick film resistors, one for current limiting LED data output, one for current limiting status LED
- 1 2x whatever 2x0603 convex resistor array - marked as 2.2k as good value, but hard package to find so use whatever, it's just current limiting a couple button inputs as a safety measure
- 2 5.1k 0603 resistors, identify USB-C device
- 1 7.5M 0805 1% or better resistor - one leg of battery level voltage divider
- 1 15M 1206 1% or better resistor - the other leg of battery level voltage divider
- 1 2x10k or 2x4.7k (or really do some math) 2x0402 convex resistor array - optional, i2c pullups, value depends on speed
- 2 10k*4 4x0603 resistor arrays - a few uses, mostly pulling up or down pins
- 1 2xR33 2x0603 convex resistor array - terminating i2c and SWD
- 2 10uH 0603 - nRF internal DCDC
- 1 2.2uH 1008/2520 inductor - DCDC
- 2 1206 ferrites - 60-120 Ohm or so should be good, USB power and shell filtering
- 2 0805 ferrites - 240 Ohm or so is fine and better for noise, much less current here, LCD analog power filtering
- 2 G-Switch GT-TC041B-H036-L1N - side mount tactile switches for power and reset buttons
- 1 of the most common top-mount SMD USB 2.0 USB-C connector there is. take your pick, seriously, they almost all will fit but the GCT USB4105 is the one the footprint's actually meant for 
- 1 2-pin horizontal PicoBlade connector - battery input
- 1 28-pin 0.5mm pitch FFC SMD connector - output to keyboard, be sure the mounting legs will fit
- 1 10-pin 0.5mm pitch FPC SMD connector - output to LCD, be sure the mounting legs will fit
- 1 JST_SH_SM03B-SRSS-TB_1x03 or similar - ARGB output
- 1 JST_SH_SM04B-SRSS-TB_1x04 or similar - Adafruit Stemma QT-like i2c output
- 1 JST_SH_SM08B-SRSS-TB_1x08 or similar - Pimoroni SP/CE-like SPI and PWM output
- 1 shitty add-on SMD connector - for Hackaday v1.69bis shitty add ons
- 6 SK6805-EC14 ARGB LEDs - picked for the 0.25mA quiescent, still even at 0% brightness the 1.5mA total will drain a 250mAh battery in under a day. be sure you use the load switch wisely
- 1 0603 LED - for a status light. have fun!
