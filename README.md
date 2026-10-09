LM399/ADR1399 reference

<img src="Images/x399 REF Schematic.png" width="1000">

<img src="Images/x399 REF-F_Cu.svg" width="10000">

<img src="Images/x399 REF-In1_Cu.svg" width="10000">

<img src="Images/x399 REF-In2_Cu.svg" width="10000">

<img src="Images/x399 REF-In3_Cu.svg" width="10000">

<img src="Images/x399 REF-In4_Cu.svg" width="10000">

<img src="Images/x399 REF-B_Cu.svg" width="10000">

<img src="Images/x399 REF.png" width="1000">

<img src="Images/x399 REF bottom.png" width="1000">

A 10 V voltage reference using LM399/ADR1399 IC.

- General features:
  - Protected from input reverse polarity and overvoltage up to 60 V
  - Protected from output short circuit and backfeed up to 30 V 
  - Extensive RLC filter on the input and linear regulator relaxes power supply requirements  
  - Common mode filters featuring guard connection make reference resilient from common mode currents (EMI)
- Precision features:
  - Uses bootstrap scheme where output opamp is powered by the output voltage, improving PSRR (DC PSRR 200nV/V without linear regulator)
  - Main divider uses 3 resistors (2 in parallel), so it is possible to build with identical value resistors
  - Supports 150 and 200 mil radial and 1206 resistors for the divider
  - Pads for trimming with fixed through hole resistors
  - Trimming with potentiometer uses scheme that can reduce the trim range to single PPM without high value resistors
  - Trimpot is used in potentiometer (ratio) mode which has better TC and stability
  - Supports most trimpots with 100mil inline lead spacing, also supports SP5-35 fine/coarse potentiometer
  - Provides low impedance to both of the opamp inputs such that chopper amps can be used without extra current noise
  - ADR1399 uses 10u/1R snubber that makes it more stable than usual 1u/5R (stable here as in control theory, not PPMs)
 
- Changes from REV A:
  - 6 layer board with inner layers for kelvin output connections
  - Changed location of LM399, so now all heat sources are on the left, moved other heat sources away from output
  - New trim scheme and new huge trimpot footprint
  - Added 7815 regulator
  - SMD pass transistor, heat disipated to case through mounting hole and radiation
  - Added circuit that turns off pass transistor periodically if output voltage is low to reset thyristor when backfeed event has ended
  - Increased output load resistor value, because the lm399 heater already provides enough minimal load
  - BOM optimization, decreased amount of different values
  - Added guard traces around inverting node
  - Increased output capacitance such that opamp should be stable without extra frequency compensation
  - Increased R15 to improve AC PSRR, this is possible because new BJT has higher current gain
  - New opamp offset trim scheme, seems sound in theory but not much info on it
  - Tantalum caps everywhere other than the very big cap
  - Added C28 "feedforward" capacitor which makes circuit gain unity at high frequency, it also removes effect of inverting node capacitance to ground on stability and gives a low impedance path for charge injection of chopper amps inverting input
  - Decreased R12 value since it was reducing DC open loop gain (downside is that now it makes less of a "zero" with C12?)
  - Changed adr1399 snubber from 1u/5R to 10u/1R after doing some experiments with different cap values
  - Added two mounting holes, finally we can have 4 (although the case still comes with only two screws :/ )
  - The board is now very double sided load, most precision stuff is on the bottom
 
