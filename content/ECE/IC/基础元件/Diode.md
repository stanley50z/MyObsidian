---
date: 2024-08-09
---
1.6
[[TAOE Master List]]

![[Diode-20240818153006676.png]]

Diode is a two-terminal passive **nonlinear** device
- nonlinear means doubling signal $\neq$ doubling response
- since it's nonlinear, circuits with diodes cannot have Thevenin equivalent

### 1.6.2 Rectifier
When diodes act as an one way conductor to only pass positive voltage
**half-wave rectifier(unfiltered)**
![[Pasted image 20240809102647.png|300]]![[Pasted image 20240809102657.png|300]]
**full-wave rectifier(unfiltered)**
![[Pasted image 20240809102725.png|300]]![[Pasted image 20240809102736.png|300]]

### 1.6.3 Power-supply filtering
**full-wave rectifier with filter**
![[Pasted image 20240809103431.png|300]]![[Pasted image 20240809103444.png|300]]
We choose a relatively large capacitor, so that $R_{load}C \gg 1/f$
	i.e. make the time constant of discharging much longer than the period of recharging

**A. Calculation of ripple voltage**
$\Delta V=\frac{I}{C}\Delta t$
Taking $\Delta t = 1/2f$(full-wave), $\large\Delta V=\frac{I_{load}}{2fC}$

### 1.6.4 Rectifier configurations for power supplies
**A. Full-wave bridge**
As discussed above. Usually, the bridge part is a prepacked module

**B. Center-tapped full-wave rectifier**
![[Pasted image 20240809105005.png|300]]
[video explanation](https://www.youtube.com/watch?v=mVzN_twa_z0)
The center of the secondary winding is grounded (center-tapped).
Due to the secondary winding split in half by the ground, it only gets half the V_in. So to get the same level of voltage, the transformer need to be 1:2

**C. Split supply**
![[Pasted image 20240809110718.png|300]]
A popular variation of the center-tapped full-wave circuit, this way the other half can be the negative V, which is useful for many applications.

**D. Voltage multipliers**
![[Pasted image 20240809113048.png|300]]
[video explanation](https://www.youtube.com/watch?v=iDQRB8DOJE4)
[webpage](https://www.kemet.com/en/us/technical-resources/voltage-doublers.html)
In each half, that side's capacitor is charged, and two capacitor in series produce double the voltage. **These kinds of configurations are for high voltage but low current**
***Cockcroft-Walton generator(for greater multiples)***
[video explanation](https://www.youtube.com/watch?v=litsAzP4oqw)
basically, it charges capacitors stage by stage. First, a capacitor get charged. Then, the charge on capacitor + V_in in series(now multiplied) is used to charge the next capacitor. Repeat this to get 1x more in each stage.

### 1.6.5 Regulators
To regulate DC input, i.e. power supply
It's not the best to use huge capacitors to regulate the ripple voltage:
- They may be bulky and expensive
- The peak voltage(of say, a sine wave) produces more $I^2R$ heat
- It still won't eliminate the influence of input fluctuation and load current on the output

Instead, a better way is to lower the ripple enough(10%, for example), then use an active feedback circuit.

Two common types are *linear regulated dc power supply* and *regulated switching power converter*

### 1.6.6 Circuit applications of diodes
**Signal rectifier**
![[Pasted image 20240810182244.png|400]]
The RC part is the differentiator. Figure 1.69 is used to detect the rising edge of a square wave.
Figure 1.70 uses another diode to compensate for three reasons:
- there is nothing to adjust
- the compensation will be nearly perfect
- changes of the forward drop (e.g., with changing temperature) will be compensated properly

**Diode gates**
![[Pasted image 20240810182648.png]]
The crossing point passes only the higher voltage without effecting the lower one(since the reversed direction is blocked by the diode). When 5V is turned off, 3V passes through

**Diode clamps**
![[Pasted image 20240810185123.png]]
Voltage more than (5V+voltage drop) is dissipated through the resistor. 
Voltage lower than this won't be effective, unless it's super negative that breaks the diode.
The tradeoff here is added resistance to the signal.
You may use a voltage divider to be the reference point(the 5V part), but it's not the best because it's not *stiff (won't bend easily)*, i.e. has low internal resistance.
Instead, transistor and op-amp are usually better.
For time-varying signals only, you can also add a *bypass capacitor* across the 1k resistor. 

**Limiter**
![[Pasted image 20240811074107.png]]
Clamps on both side, so the output is $\pm$(voltage drop of the diode)
This may seem small, but could prevent a high-gain amplifier to saturate later in the circuit

**Diodes as nonlinear elements**
![[Pasted image 20240811084138.png|300]]![[Pasted image 20240811084146.png|282]]
Current through a diode is proportional to an exponential function of the voltage across it at a given temperature. So the output voltage is proportional to the log of current.

### 1.6.7 Inductive loads and diode protection
[inductive load](https://www.allaboutcircuits.com/textbook/direct-current/chpt-15/magnetic-fields-and-inductance/)
![[Pasted image 20240811092308.png]]![[Pasted image 20240811092314.png|315]]
At the moment of power switching off, the inductor tries to force the current to flow by adding voltage to B, which may damage the component. Instead, in Figure 1.84, the voltage at B is maintained one voltage drop above the supply voltage. Of course, the diode should be able to handle the current and reverse voltage
![[Pasted image 20240811093946.png]]
For AC, the diode solution doesn't work, and we uses a RC "snubber" instead.

### 1.6.8 Interlude: inductors as friends
Charging capacitor through resistor(***resistive charging***) loses energy and produces heat.
Charging through inductor(**resonant charging***) is lossless.
![[Pasted image 20240811100219.png]]
Without the diode, LC oscillates back and forth, but with diode, output stays at 2V

