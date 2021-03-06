# Serial Communication and I2C Protocols
## What is serial communication?
To transfer data from one system to another there are mainly two ways, **serial communication** and **parallel communtication**. As the name suggests, in serial type, the data is sent in a series form whereas in the parallel type the data is sent in a parallel type. What this means is that in parallel type, we would require a lot of wires connected between the systems which although **very fast** but is often **not feasable**. The serial type on the other hand sends the data in a serial order which therefore requires one cable for data transfer and one or two other for earthing etc. Hence we can deduce that this method is quite **slow** as compared to the other way but **is feasible**.<br><br>
Serial Communication is a process of sending data 1 bit at a time sequentially over a communication channel. This the way the Arduino board communicates to the computer. Serial Communication is used when we send a commond from computer to Arduino board and vice-versa. Thus, uploading a code uses the same. The LEDs (present on Arduino) **RX** and **TX** flash when the arduino receives data and transmits data respectively.<br>
A simple Arduino code:
~~~
void setup() {
Serial.begin(9600);
}

void loop() {
Serial.print('1');
delay(200);
}
~~~
Output:<br>
![Serial Communication](https://cdn.instructables.com/FOO/XDSD/J7JMSYT1/FOOXDSDJ7JMSYT1.LARGE.jpg?auto=webp&frame=1&fit=bounds)<br>
The above picture shows the Serial Output for the code.
## What is I2C Protocols?
**I2C** _(pronounced I square C)_ or **Inter-Integrated Circuit** is a serial protocol for two-wire interface to connect low-speed devices like *microcontrollers, EEPROMs, A/D and D/A converters, I/O interfaces* and other similar peripherals in embedded systems. I2C bus is popular because it is simple to use, there can be more than one master, only upper bus speed is defined and only two wires with pull-up resistors are needed to connect almost unlimited number of I2C devices. <br><br>
![I2C](http://quanser-update.azurewebsites.net/quarc/documentation/i2c_protocol_diagram.gif)<br><br>
Each I2C slave device needs an address. Each slave device has a unique address. Transfer from and to master device is serial and it is split into 8-bit packets. All these simple requirements make it very simple to implement I2C interface even with cheap microcontrollers that have no special I2C hardware controller. You only need 2 free I/O pins and few simple i2C routines to send and receive commands.
### I2C Interface
I2C uses only two wires, **SDA** (*serial data*) and **SCL** (*serial clock*). SCA has the purpose of producing a synchronic wave or the clock wave, whereas SDA is a digital wave containing data in form of bits.
### I2C Address
I2C generally uses 8-bit data transmission. The first 7-bits are the address bits which contains the address of the slave devices, followed by the 8th-bit which indicates *read* or *write*. This forms the **Control Byte**.
### I2C Protocols
The protocol begins with a *start signal* by the master device which is followed by the *Control Unit*. After every 9th clock cycle we either have an *Acknowledge (ACK)* bit or *Not Acknowledge (NACK)* bit. Further running depends on this. If the bit is ACK, the next 8-bits contain the data sent by the Master device which is again followed by ACK or NACK. When NACK is encountered, it is considered as an end sign.
### Conclusion
I2C bus is used by many integrated circuits and is simple to implement. Any microcontroller can communicate with I2C devices even if it has no special I2C interface. I2C specifications are flexlible – I2C bus can communicate with slow devices and can also use high speed modes to transfer large amounts of data. Because of many advantages, I2C bus will remain as one of the most popular serial interfaces to connect integrated circuits on the board.
