# Components & Costs #
| **Component** | **Price** |
|:--------------|:----------|
| LEGO Mindstorms NXT v2 Retail Kit | 300 EUR   |
| LEGO Extra components (9695) | 90 EUR    |
| LEGO Racks (x7) | 15 EUR    |
| Spare LEGO Parts | _Undefined_ |
| **TOTAL**     | **405 EUR** |

# Motors #
Three motors are being used to control the machine, plus a DC motor to control the drill attached on the Z axis

| **Motor** | **Axis** |
|:----------|:---------|
| A         | x        |
| B         | y        |
| C         | z        |
| DC        | Drill    |



## Linear Actuator ##

During construction the need for linear actuation arose, especially when moving the Z-axis vertically. A DIY Linear Actuator was built and the concept behind it was pretty simple.

![http://cache.lego.com/upload/contentTemplating/Technic2DesignersBlog/images/pic22A283FAF500F6BC302B7E158B20DD9D.png](http://cache.lego.com/upload/contentTemplating/Technic2DesignersBlog/images/pic22A283FAF500F6BC302B7E158B20DD9D.png)

In detail; a simple 8-tooth Gear was put between a Worm and a Linear (rack) Gear to establish linear movement along the Z-axis.

# External Power Supply #
The NXT Brick was modified in order to be supplied by an AC/DC adapter.
The steps of the modification are shown below:
https://plus.google.com/photos/114793832022163550064/albums/5762426204029005921

> Remove the 6 batteries and uncover the NXT. On its cover, cut the latch at the centre of its narrow side.

  1. Supply with an AC/DC which provides with power intensity higher than 1A. Set voltage to 9V.
  1. Purchase a female connector, screw terminal and wires. Find the polarity of the adapter and connect the components.
  1. Glue (if possible) the female connector in the side of NXT, as shown
  1. Connect the wires at NXT's terminals [+ (V), - (GND)] and re-cover the NXT.






# Drill #

## Controlling the drill via TWI (I2C) ##

The drill can be controlled via Two-Wire Interfaces (TWI). Here, the I2C Interface is used.
leJOS has a class under the name `I2CSensor.java` which is capable of handling I2C-bus devices.

# Pull-up Resistors #

10kΩ are used



## Control over Relay (NOT RECOMMENDED) ##

### Schematic ###

![http://s8.postimage.org/ajhbd291x/drill_control_over_relay.png](http://s8.postimage.org/ajhbd291x/drill_control_over_relay.png)

As shown above, the drill is controlled via a SPST Relay. It uses the following NXT Pins



| **Pinout** (OUTPUT Port) |
|:-------------------------|
| #                        | Name                     | Function                 | Description              |
| 1                        | 9V                       | Analog interface         | +9V Supply               |
| 2                        | GND                      | Ground                   | Negative Pinout (Ground) |


which make it able to interact with the SensorPort Class and classes developed for its implementation.