<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

This design is a 4-to-1 multiplexer (MUX) with some unique, built-in logic and 
display features.
It takes four input signals and produces one main output, but unlike a traditional MUX, it doesn’t require external address selection lines.
 
|		Inputs		|			Outputs			|
|-------------------|---------------------------|
|		clk			|			MUX_out			|
|		rst			|	'a'-7-segment display	|
|		INO			|	'b'-7-segment display	|
|		IN1			|	'c'-7-segment display	|
|		IN2			|	'd'-7-segment display	|
|		IN3			|	'e'-7-segment display	|
|		EN			|	'f'-7-segment display	|
|					|	'g'-7-segment display	|


## How to test

#Internal Operation

The design includes a 2-bit counter.

A clock (CLK) input drives this counter:

On each rising edge of the clock, the counter increments.

The counter value automatically selects which of the four input channels (IN0–IN3) 
is routed to the output.

Therefore, the MUX automatically cycles through all inputs sequentially, 
without needing external address control.

#Display Conversion

In addition to the MUX output, the design provides a 7-segment display interface.

The 2-bit counter value (00, 01, 10, 11) is internally decoded into the 
corresponding 7-segment pattern.

This allows the user to visualize which input channel is currently active directly 
on a display.

Example:

|		Counter	|			Value	Selected Input		| 7-Segment Display |
|----------|-------------------------|-------------------|
|    00    |           IN0           |        "0"        |
|    01    |           IN1           |        "1"        |
|    10    |           IN2           |        "2"        |
|    11    |           IN3           |        "3"        |


#Enable Function

The design also includes an Enable (EN) pin:

When EN = 1 (HIGH) → the counter CLK, MUX output, and 7-segment display are active.

When EN = 0 (LOW) → all outputs and CLK are disabled. Counter outputs preserved.

#Reset Function

The reset pin resets the counter to output 0, consequently resetting the seven segments
display to zero.

## External hardware

Seven segments display
