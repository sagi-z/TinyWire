# Arduino TinyWire Slave Library (FC is Flow Control)

Originals from <http://www.arduino.cc/playground/Code/USIi2c>

Modified to support ATtiny44/84

__Modified to disable callbacks (hence no clock stretching) and implement flow control in a library for usage by a single master raspberry pi system.__

* Example master code is in (**TODO**)
* Raspberry Pi master flow-control layer code is here, in the PiI2C_FC (**TODO**)
* Full usage tutorial is here (**TODO**)

## NOTE about reliable communication

__UPDATE__: This branch, when comitted, will enable writing I2C slave code which does not strech the clock and hence is 100% reliable with the raspberry pi (verified on Pi2 and Pi3). Tests with a slave on the ATtiny84@8MHZ(internal) reached 240K bits per second of __data__ (30K bytes per second of __data__ received by the Pi I2C master!) with 0% errors, using almost nothing of the CPU resources.

For an example Pi master code working at 240Kbps with the *FastSafeSlave.ino* and Pi3 example see here (**TODO**)

__What's written below about the clock stretching is true if you use the original coding style, but this repository avoids the reliability issues related to clock-streching of the salve as mentioned above.__

~~Since (most of) the ATTinys lack TWI module for implementing all the nitty-gritty of I2C in hardware
they will have to do some clock-stretching (at least if run at 8MHz, you may get away with more on higher clock speeds)
as specified in the I2C protocol. However some (especially "bit-banged") master implementations do not
support clock-streching (looking at you Bus pirate 3.x and [RPI][rpibug]), you will not get reliable communication
unless your master supports the full I2C protocol spec. There is a [library][pigpio] which can bit-bang I2C correctly on RPI, use that instead of the [buggy hardware][rpibug] (thanks to @brendanarnold for [that tip][pigtip]).~~

~~You can use my [Arduino based I2C master][i2crepl] to test your TinyWire code, this uses Bus Pirate semantics
with Arduinos TWI hardware that is known to implement I2C properly.~~

~~[i2crepl]: https://github.com/rambo/I2C/blob/master/examples/i2crepl/i2crepl.ino~~
~~[rpibug]: http://www.advamation.com/knowhow/raspberrypi/rpi-i2c-bug.html~~
~~[pigpio]: http://abyz.co.uk/rpi/pigpio/python.html#bb_i2c_zip~~
~~[pigtip]: https://github.com/rambo/TinyWire/issues/14#issuecomment-125325081~~

