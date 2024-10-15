---
date: 2024-09-29
---
## Op-Amp
**Non-Ideal model**
$\large V_{out}=A(V_{+}-V_{-})$
### Diode: Exponential Model
$\large I_{D}=I_{S}(e^{V_{D}/V_{T}}-1)$   Can derive $\large V_{D}\approx V_{T}\ln(I_{D}/I_{S})$
**Iterative method**
- Guess $\large V_{D}$, usually 0.7v
- Calculate $\large I_{D}$ with \*\*KVL\*\*, and use the value and formula to derive V_D
- Repeat until converge
### MOSFET
**Cut-off**: $\large V_{GS}<V_{THN}$
**Triode**: $\large V_{DS}<(V_{GS}-V_{THN})$
$\large I_{DS}=\frac{K}{2}[2(V_{GS}-V_{THN})V_{DS}-VDS^2]$
**Saturation**: $\large V_{DS}>(V_{GS}-V_{THN})$
$\large I_{DS}=\frac{K}{2}(V_{GS}-V_{THN})^2$
### Capacitor                                  Inductor
$\large E=1/2VC^2$                                          $\large E=\frac{1}{2}LI^2$
$\large Q = CV$
$\large i_{C}(t)=C\frac{dV_{C}}{dt}$                                         $\large V=L\frac{dI}{dt}$
**RC Circuit**: $\large \tau=R\cdot C$                               **RL Circuit**: $\large \tau=\frac{L}{R}$

$\large i(t)=(I_{HI}-I_{LO})(1-e^{-t/\tau})+I_{LO}$
### The magnitude of time-varying equation is the difference between initial and final value
