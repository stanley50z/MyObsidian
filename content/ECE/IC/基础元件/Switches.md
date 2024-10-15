---
date: 2024-08-17
---
1.9.1
Master List: [[TAOE Master List]]

### 1.9.1 Electromechanical devices: switches
**Toggle switches**
![[Switches-20240817105025921.png]]
SPST: single-pole single-throw switch
SPDT: single-pole double-throw switch
DPDT: double-pole double-throw switch

**Pushbutton switches**
![[Switches-20240817105011149.png]]
[Understanding Form A, Form B, Form C Contact Configuration - Electromechanical / Relays - Electronic Component and Engineering Solution Forum - TechForum │ DigiKey](https://forum.digikey.com/t/understanding-form-a-form-b-form-c-contact-configuration/811)
NO: Normally open, NC: Normally closed
always "break before make"

**Rotary switches**
Multiple poles and positions
Have both "shorting" type(make-before-break) and "non-shorting" type(break-before-make)
- Shorting type is preferred when you don't want open circuit between switch positions
- Non-shorting type is preferred when you want switch positions to ever connect
Sometimes you just want to know the degree of the switch turned. Common solutions are the switch encoding itself to binaries, or use a rotary encoder.

**PC-mounting switches**
PC: printed-circuit boards
often called DIP switches, but modern ones increasingly use the more compact SMT package
DIP: dual in-line package
SMT: surface-mount technology
[DIP switch - Wikipedia](https://en.wikipedia.org/wiki/DIP_switch)

**Other switch types**
- Hall-effect switch
- reed switch
- proximity switch

> It’s always OK to operate a switch below its maximum ratings, with one notable exception: since many switches rely on substantial current flow to clean away contact oxides, it’s important to use a switch that is designed for “dry switching” when switching low level signals; otherwise you’ll get noisy and intermittent operation (see Chapter 1x).

**Example**
![[Switches-20240817111643977.png]]




**Relays are primarily used when the controller and controlled circuit needs to be completely isolated**
- example: small voltage circuit controlling high voltage circuit

