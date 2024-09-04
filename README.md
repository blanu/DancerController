The 2N7002 transistor is an N-channel Power MOSFET.

With an N-channel MSOFET, the current flows from the drain to the source.
The source should be connected to ground.
The drain should be connected to the load.
To turn it on, the gate voltage must be more positive than the source voltage.
An important consideration in a MOSFET is the voltage difference it can handle between the drain and the source.
For The 2N7002, the maximum voltage difference tolerated is 60V.
Radio key jack voltages vary, but 60V should be sufficient.

The gate threshold voltage is how much the gate needs to be above the source in order to turn on, which for the 2N7002 is 1-2.5V.
Since the source should be connected to ground at 0V, that means that the activation voltage is 1-2.5V.
Therefore, the MOSFET switch will be open with the gate voltage is 1-2.5V and closed when the voltage is less than 1V.
The maximum voltage of a 3.3V microcontroller is 3.3V, so a resistor is needed to lower max voltage to between 1 and 2.5V.
This is both for the safety of your MOSFET and so that you can use digital microcontroller output pins instead of the more
limited in number analog output pins. However, if analog output pins are available then you could make do with setting the voltage
to 50%, which on many Arduinos I have worked with would be around 512 as an analog output value. However, check the specs of your
specific Arduino to determine how to achieve an output voltage within the tolerated range.

A 10K pull-down resistor between gate and source is used to drain away stray capacitance from the user that could otherwise
trigger the gate spuriously. A pull-down resistor ensures that the gate is either high or low and not floating.

A 1K resistor between the microcontroller and the gate decreases the current to the gate, which also decreases the rise and
fall time. It is also required to have SOME resistor in order to get the gate to work because the gate acts as a capacitor.
Adding a resistor allows you to more easily calculate the current flowing to the gate and therefore the switching time. otheriwse,
only the parasitic resistance of the circuit is in play, which is unknown. Another reason to add a resistor is to reduce
oscillations that can make the on-off transistion rough.

A zener diode from ground to the gate pin protects from overvoltage on the pin.


