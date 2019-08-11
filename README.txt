------------------------------GOALS--------------------------------------------


0) understand a way to save a bit in memory.

1) create a link with the previous lab work: the use of serial data transfer.
	ex: U(S)ART...

2) understand how with a limited amount of I/O pins (2 or 3 today), you could
 control a much greater number of pins / devices / LEDs in our case. (8 or 16 today).

3) debounce a switch button, either using a RC circuit, or a latch…


------------------------------STEPS--------------------------------------------

1) understand the latch concept:
understand the truth table of an OR gate and an AND gate.
(similar to '|' and '&' bitwise operators)
understand the truth table of an NOR gate.
a ‘bubble’ represents an invertion ('~' symbol in bitwise operations. '!'symbol in c...)
build a NOR latch or a NAND latch

S stands for set (binary 1)
R stands for reset (binary 0)
Q is the output that we want.
_
Q is thh complement of Q.

understand the race condition concept... we will fix this problem!

we just saved a bit in memory! 1 or 0!

2) build your own inverter with a NAND gate:
resource: http://nandgame.com/  --> you only need to succeed the very first step.
	  ______
input = OUTPUT						
(the notation says un-complemented(input)/complemented(output), keep it in mind...)

3) build a D latch with a combination of step 1 and step 2.
let’s avoid the racing condition...

4) the clock signal comes in: build a clocked SR latch:
if (D == 1 && CLK == 1) something happens
or if (D == 0 && CLK == 1) something happens
else	nothing happens!

5) you could build an edge triggered D flip-flop if you like pain and misery
but… just don’t.

nb: on the schematic a double inversion cancels itself*
(going through inversion gates only adds some propagation delay time for the
signal… - which you can find in the datasheet(s) - that does not affect us today at all).


6) take another look at the schematic showing the edge triggered D flip flop with preset
and clear inputs

7a) what is a register?
it can store a word in memory (several bits).

7b) SHIFT REGISTERS (sort of similar to the bitwise operators '>>' or '<<')
note: SIPO (serial in/parallel out)
we are going to control 8 LEDs with only 3 controlled inputs (understand 3 pins from your MCU…).
- serial in
- clock	
- latch (paralelle out. releases the informations stored in the register)
--> use push buttons to control each of them.

Try to store bytes and connect each output to an LED for debugging.
Try to burn LEDs
Try to not burn LEDs.

8) do you need to debounce a button? Which one?

understand the concept of debouncing.
Either debounce it using a latch or a RC circuit, your choice.

note: (not useful for today)
a JK flip-flop is really similar to what we have done with the RS flip-flops… 
another way to debounce/have edge-triggered information is to put two of them in a raw. it makes
a master-slave JK flip flop, it avoids using capacitors which is not appropriate for very small
Integrated Circuits.

9) the concept of daisy chaining: the input of number n+1 is the output of number n

We are going to control 16 LEDs with only... 3 controlled inputs!

10) succeed in latching the words 0xCAC9 then 0x4242.


------------------------------CONGRATS!----------------------------------------

- simulated serial protocol coming in
- 16 LEDs controlled with only 3 simulated output pins.
- button(s) debounced.
				
					well done!
					
					charmstr

