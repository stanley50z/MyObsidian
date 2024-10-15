---
date: 2024-07-20
---
1.2.5
Master List: [[TAOE Master List]]

Thevenin's theorem states that any two-terminal network of resistors and voltage sources is equivalent to a single resistor R in series with a single voltage source V.

$V_{Th}=V$ (open circuit)
$R_{Th}=\frac{V_{open}}{I_{short}}$
or, make voltage source short circuit and current source open circuit, and get the equivalent resistance looking into the two poles

By measuring open circuit voltage and close circuit current, you get the Thevenin equivalent $R_{Th}$.
(internal resistance, source resistance, Thevenin equivalent resistance all mean the same thing)
**Circuit loading**
Attaching a load whose resistance is less than or even comparable to the internal resistance will reduce the output significantly. This is called "Circuit loading".

Therefore, generally, you would want $R_{load}\gg R_{internal}$, because then you would have little affect on the source.

**for finding the equivalent resistance, can also use this**
![[Thevenin equivalent circuit-20240829105011104.png]]