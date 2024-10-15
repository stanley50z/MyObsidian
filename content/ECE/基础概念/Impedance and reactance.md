1.7
[[TAOE Master List]]
### 1.7 Impedance and reactance
Capacitors and inductors are **linear**, meaning that the output amplitude is directly proportional to the input amplitude. This also means:
- If the input is a sine wave, the output is also a sine wave, *at the same frequency*

**Impedance** (Z) is the “generalized resistance”
*Reactive* devices like inductors and capacitors are always out of phase. They have **reactance(X)**
*Resistive* devices like resistors are always in phase.
[[电抗，阻性器件]]
> $Z = R+jX$

*For a single-frequency sine wave input*, you can generally replace "resistance" with "impedance" when analyzing the circuit. 

### 1.7.1 Frequency analysis of reactive circuits
**RC Low/High pass filter**
A good enough approximation to treat capacitors as frequency-dependent resistors, with reactance $X_{c}=\frac{1}{\omega C}=\frac{1}{2\pi fc}$
Cutoff frequency $f_{c}=\frac{1}{2\pi RC}$, where the gain is -3dB because it's the half-power point, -3dB=20*log(1/$\sqrt{ 2 }$)

**Blocking capacitor**
A common one is a *dc blocking capacitor*, and the crossover frequency is below all frequencies of interest.
![[Pasted image 20240811155615.png|399]]
When choosing the R value, make sure it's higher(maybe 10x) than the input impedance, and make sure the output impedance is higher than R.
> So a signal source’s impedance should generally be small compared with the impedance of the thing being driven.
### 1.7.2 Reactance of inductors
$X_{L}=\omega L=2\pi fL$
- unlike capacitor, the reactance increases as the frequency increases.
Blocking high frequency and passing DC and low frequency.

### 1.7.3 Voltages and currents as complex numbers
We can use complex numbers to represent voltage and current, again in a steady frequency sine wave.

**Real to complex**
Voltage $\large V_{0}\cos(\omega t+\phi)$ can be represented by $\large V_{0}\,e^{j\phi}$
and $\large e^{j\phi}=\cos \phi+j\sin \phi$
where $j=\sqrt{ -1 }$, which replaces the math convention $i$ because of possible confusion

**Complex to real**
Multiply the complex number representation by $\large e^{j\omega t}$, and **take the real part**.
For example, for a voltage whose complex representation is $\large V=5j$
	$\large  V(t)=5j\cdot(\cos \omega t+j\sin \omega t)=-5\sin \omega t+5j\cos \omega t$
	Take the real part, $\large V(t)=-5\sin \omega t$

### 1.7.4 Reactance of capacitors and inductors
**Reactance of capacitors**
$\large V(t)=V_{0}e^{j\omega t}=V_{0}(\cos \omega t+j\sin \omega t)$
$\large I(t)=C\left( \frac{dV(t)}{dt} \right)=C\left( \frac{d(V_{0}e^{ j\omega t })}{dt} \right)=CV_{0}\left( \frac{d(\cos \omega t+\sin j\omega t)}{dt} \right)$
	$=C\omega V_{0}(-\sin \omega t+j\cos \omega t)=C\omega V_{0}e^{ j\omega t }\cdot j$
$\large Z_{C}=\frac{V}{I}=\frac{1}{j\omega C}=-\frac{j}{\omega C}=-jX_{C}$
If the circuit is only capacitors and inductors, then the impedance$\large Z_{C}$ is just reactance $\large X_{C}$ with a factor of $\large -j$ to account for the 90 degree leading phase shift of current versus voltage.

**Reactance of inductors**
Similarly, $\large Z_{L}=j\omega L=jX_{L}$

### 1.7.5 Ohm’s law, KCL, KVL generalized
**Ohm's law**
Instead of $\large  V=I\cdot R$, $\large V=I\cdot Z$
The calculations follow the same rules as resistance.
	$\large  Z = Z_{1} + Z_{2}$ in series, $\large  Z=\frac{1}{\frac{1}{Z_{1}}+\frac{1}{Z_{2}}}$ in parallel
	$\large  Z_{R}=R, Z_{C}=-\frac{j}{\omega C},Z_{L}=j\omega L$

**KCL & KVL**
the sum of the ***(complex)*** voltage drops around a closed loop is zero
the sum of the ***(complex)*** currents into a point is zero

**Magnitude calculation**
If we just want the magnitude, then we can simply use the magnitude of those complex numbers instead of doing complex algebra
![[Pasted image 20240812163824.png]]

### 1.7.6 Power in reactive circuits
The instantaneous power delivered is always $\large P=VI$, but V and I are not simply proportional in reactive circuits.
Average power: $\large \frac{1}{T}\int_{0}^{T}V(t)I(t)dt$
The other way is $\large P=\mathrm{Re}(VI^*)=\mathrm{Re}(V^*I)$
	where V and I are complex rms amplitudes, and \* means [[complex conjugate]]
**power factor** is $\large\text{power factor}=\frac{\text{power}}{|V||I|}$

### 1.7.7 Voltage dividers generalized
Now, either or both the resistors of our original divider can be replace by capacitors or inductors.
![[Pasted image 20240813105355.png]]
$\large I=\frac{V_{in}}{Z_{total}}=\frac{V_{in}}{Z_{1}+Z_{2}}$  and $\large V_{out}=IZ_{2}=V_{in}\frac{Z_{2}}{Z_{1}+Z_{2}}$

### 1.7.8 RC highpass filters
![[Pasted image 20240813120237.png]]
$\large V_{out}=V_{in}\frac{Z_{2}}{Z_{1}+Z_{2}}=V_{in}\frac{R}{R-\frac{j}{\omega C}}=V_{in}\frac{R(R+j/\omega C)}{R^{2}+(1/\omega^{2}C^{2}) }$
$\large |V_{out}|=\sqrt{ V_{out}V_{out}^* }=V_{in} \sqrt{ \frac{R^4+\frac{R^2}{\omega^{2}C^{2}} }{\left( R^{2}+\frac{1}{\omega^{2}C^{2} } \right)^2}}=V_{in} \sqrt{ \frac{R^{2}\cdot\left( R^{2}+\frac{1}{\omega^{2}C^{2} } \right)}{\left( R^{2}+\frac{1}{\omega^{2}C^{2} } \right)^2}}=V_{in}\frac{R}{\sqrt{ R^{2}+\frac{1}{\omega^{2}C^{2} }}}$
![[Pasted image 20240813160056.png]] $\large =V_{in}\frac{Z}{Z_{total}}$

### 1.7.9 RC lowpass filters
![[Pasted image 20240813175248.png]]
At low frequency, C acts as an open circuit, therefore:
- the signal driving the filter($\large V_{in}$) sees R + load resistance
- the load sees R (if $\large V_{in}$ is viewed as perfect AC and therefore has zero impedance, then view $\large V_{in}$ as shorted to GND)
At high frequency, C acts as shorted, therefore:
- The driving signal sees just R
- The load signal sees zero impedance because the capacitor shorts to GND.

### 1.7.10 RC differentiators and integrators in the frequency domain
RC differentiator is the same as the RC highpass filter.
Similarly, RC integrator is the same circuit as the RC lowpass filter.
The differentiator/integrator form is when we think of waveforms in time domain, while filters are for responses in time domain.

For differentiators, we should select RC values so that $\large \frac{dV_{out}}{dt}\ll \frac{dV_{in}}{dt}$. In frequency domain, this means that the signal frequency must be $\large \ll$ 3dB.
Similarly, for integrators, the lowest signal frequency should be well above 3dB.

### 1.7.11 Inductors versus capacitors
RL can also make filters, but they are rare in practice because:
- inductors tend to be bulky and expensive
- the performance is less ideal than capacitors
**One important exception** is the use of ferrite beads and chokes in high-frequency circuits.
Other usage: LC tuned circuits, switch-mode power converters

### 1.7.12 Phasor diagrams
A phasor diagram can clarify why the cutoff frequency is at -3dB, not -6dB when $\large -6dB\to \frac{A_{2}}{A_{1}}=10^{\frac{-6}{20}}\approx \frac{1}{2}$
[[Signals]]
One way to think about this is that the cut off frequency is the half-power spot, so you use the dB equation for power instead, which gives -3dB. [Quora link](https://www.quora.com/Why-is-the-cutoff-frequency-selected-at-3dB-in-a-low-pass-filter#:~:text=The%203%20dB%20point%20is,power%20is%20lower%20than%2050%25.)

Another way is to look at the phasor diagram, and think of the 3dB frequency as the spot when the reactance of the capacitor is equal to the resistance of the resistor(magnitude).
![[Pasted image 20240815104821.png]]
In graph A, the hypotenuse(斜边) represents the input voltage, and it's magnitude is impedance(and since current is the same everywhere, the magnitude is proportional to the magnitude of voltage as well).
And the right-angles sides are the impedances of R and C. Them combined, it's obvious to see that the input is proportional to $\large R\sqrt{ 2 }$, comparing to $\large R$ of one component, making the output voltage $\large \frac{1}{\sqrt{ 2 }}$in magnitude.

### 1.7.13 “Poles” and decibels per octave
dB/octave is used to describe the behavior of a filter beyond the cutoff. A simple RC filter has a 6dB/octave falloff. Two RC sections get you 12dB/octave, three get you 19dB/octave, and so on. You can also call them "two-pole filter", "three-pole filter", etc. 
Note that you can't simply connect identical RC filters and expect separated and consecutive behavior, because one would have significant loading effect. Remember that the load should have a much higher impedance.

### 1.7.14 Resonant circuits
**Parallel LC circuit(bandpass filter)**
![[Pasted image 20240815111719.png]]
The LC combined impedance is $\large Z_{LC}=\frac{j}{\left( \frac{1}{\omega L}-\omega C \right)}$
At resonant frequency $\large f_{0}=\frac{1}{2}\pi \sqrt{ LC }$, $\large \omega=\frac{1}{\sqrt{ LC }}$, then $\large Z_{LC}=\frac{j}{\frac{\sqrt{ L\mathbb{C} }}{L}-\frac{C}{\sqrt{ LC }} }=\frac{j}{\sqrt{ \frac{C}{L} }-\sqrt{ \frac{C}{L} }}\to \infty$
which make $\large V_{out}\approx V_{in}$

**Series LC**
![[Pasted image 20240815122340.png|422]]
By calculation, $\large Z_{LC}\to 0$ at resonant frequency, so it behaves oppositely.
![[Pasted image 20240815122818.png|358]]![[Pasted image 20240815122845.png|400]]
The *quality factor* Q is a measure of the sharpness of the peak, $\large Q=\frac{f_{o}}{\Delta f_{3dB}}$
For parallel RLC, $\large Q=\omega_{0}RC$. For series RLC, $\large Q=\omega_{0} \frac{L}{R}$

### 1.7.15 LC filters
![[Impedance and reactance-20240815173512970.png]]![[Impedance and reactance-20240815173540722.png]]
LC filters in application.
Figure 1.112 shows how LC filters work much better than RC filters
[LC vs RC low pass filter, what's the difference? : r/electronics](https://www.reddit.com/r/electronics/comments/ec64z/lc_vs_rc_low_pass_filter_whats_the_difference/)
### 1.7.16 Other capacitor applications
Usages of capacitors

**Bypassing**
[How does a bypass capacitor work and what does it do? : r/AskElectronics](https://www.reddit.com/r/AskElectronics/comments/bwxk9m/how_does_a_bypass_capacitor_work_and_what_does_it/)
[EEVblog #859 - Bypass Capacitor Tutorial - YouTube](https://www.youtube.com/watch?v=BcJ6UdDx1vg)
Used to pass AC noise (usually to the ground)
![[Impedance and reactance-20240815181949234.png|402]]

**Power-supply filtering**
Basically another form of bypassing. As reddit says, you describe it based on the main purpose of the capacitor.
> If it's primary purpose is to reduce noise it's referred to as a "bypass" cap; if it's primary purpose is to store DC, it's referred to as a "reservoir" cap.
- referred as "storage" capacitor in the book

**Timing and waveform generation**
Waveform: charging and discharging the capacitor
Timing: capacitor can delay the signal.

### 1.7.17 Thevenin’s theorem generalized
Old one: [[Thevenin equivalent circuit]]
> Any two-terminal network of resistors and voltage sources is equivalent to a single resistor R in series with a single voltage source V

New one: : any two-terminal network of resistors, capacitors, inductors, and signal sources is equivalent to a single complex impedance in series with a single signal source.