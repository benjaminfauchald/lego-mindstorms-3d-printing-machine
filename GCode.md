# Letter Addresses (or G-Code Fields) #

| **Field** | **Functionality** |
|:----------|:------------------|
| Gnnn      | Standard G Code command|
| Mnnn      | Miscellaneous commands' field  |
| Tnnn      | Define tool (in this case it is only one)  |
| Xnnn      | X coordinate field  |
| Ynnn      | Y coordinate field  |
| Znnn      | Z coordinate field  |
| Fnnn      | Feedrate (speed in deg/sec) |
| Pnnn      | Time (in msec)    |
| Rnnn      | Radius (not used at the moment)|
| Nnnn      | Command queue number  |




# G-Codes #


| **Command** | **Name** | **Description** | **Parameters** | **Used** | **Example** |
|:------------|:---------|:----------------|:---------------|:---------|:------------|
| G0          | Rapid Positioning | Move Rapidly to point M(x,y,z) | X,Y,Z,F        | Yes      | G0 X23 Y34 F200 |
| G1          | Linear Interpolation | Controlled move in a straight line to point M(x,y,z) | X,Y,Z,F        | Yes      | G1 X32 F50  |
|G2           | Circular Interpolation | Controlled circular move towards an arc CW | X,Y,Z,R,F      | Yes      | G2 X20 [R2](https://code.google.com/p/lego-mindstorms-3d-printing-machine/source/detail?r=2) |
| G3          | Same as above but CCW |                 |                | Yes      | G3 X20 [R2](https://code.google.com/p/lego-mindstorms-3d-printing-machine/source/detail?r=2) |
| G4          | Dwell    | Do nothing for a defined time (in msec) | P              | Yes      |  G4 P300    |
| G17         | XY Plane |                 |                | No       | G17         |
| G18         | XZ Plane |                 |                | No       | G18         |
| G19         | YZ Plane |                 |                | No       | G19         |
| G20         | Coordinates to in | All units are now in Inches (UK Metric System) |                |  No      | G20         |
| G21         | Coordinates to mm | All units are now in Millimeters `10^(-3) m ` (S.I.) |                | No       | G21         |
| G28         | Move to origin | Move to zero endstops _You can define which axis would be zeroed_ | X,Y,Z          | Yes      | G28 X0 Z25.4 |
| G90         | Absolute Positioning System | Programming from now on will be employed in Absolute Positioning System (APS) |                | Yes      | G90         |
| G91         | Relative Positioning System | Programming from now on will be employed in Relative Positioning System (RPS) |                | Yes      | G91         |

_Codes with command numbers less than 10 can be written by adding a 0 (zero) in front of them. e.g. G1 is the same as G01_





# Positioning and Measurements #
## Absolute Positioning System (APS) ##

In APS the set of all points is described relative to the starting point (a.k.a. the "home point" `W`). An example will be more comprehensive:

| **Point** | **X** | **Y** | **Z** |
|:----------|:------|:------|:------|
| W         | 0     | 0     | 0     |
| A         | 24    | 10.5  | 30    |
| B         | 30    | 15    | 32    |

## Relative Positioning System (RPS) ##

In RPS all coordinates are relative to the last position.


_You must define the Unit System you're working with (Inches or Millimeters)_

## Units (Inches) ##

The usage of Inches (in) as a unit for length is at the momment being used only in UK.

### 1in is equal ###

| **SI units** |
|:-------------|
| 0.0254 m     | 25.4 mm      |
| **US customary/Imperial units** |
| 1⁄36 yd      | 1⁄12 ft      |


## Units (Millimeters) ##

The usage of Millimeters (mm) as a unit for length is used worldwide as a submultiple of `1m (S.I.)` and it is equal to `1/1000 m`

# M-Codes #


| **Command** | **Name** | **Description** | **Parameters** | **Used** | **Example** |
|:------------|:---------|:----------------|:---------------|:---------|:------------|
| M0          | Stop     | Scheduled machine pause |                | Yes      | M0          |
| M1          | Sleep    | Optional machine sleep |                | Yes      | M1          |
| M2          | Finish   | End of program  |                | Yes      | M2          |
| M6          | Tool Change |  _Only one tool is available_ |                | No       |             |
| M30         | Loop Program | Ends the current program and returns to its beginning |                | Yes      |             |

# T-Codes #


| **Command** | **Name** | **Description** | **Parameters** | **Used** | **Example** |
|:------------|:---------|:----------------|:---------------|:---------|:------------|
| T1          | Tool #1  | _The only tool being used for the time being_ |                | No       | T1          |


---

# Examples #

## Table of Points ##

| **Point** | X | Y | Z |
|:----------|:--|:--|:--|
| W         | 0 | 0 | 0 |
| 1         | 10 | -10 | 2 |
| 2         | 9  | 12 | 4 |

## Code ##

```
T1 
G0 X10 Y-10 Z2 F200
G1 X9 Y12 Z4 F150
M3
```