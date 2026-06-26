## This are some of the thing that we need to keep in mind during building this 

For more details follow this - https://lasergrbl.com/usage/arduino-connection/

### I have use an unique way to setup software with extreme precision I went online searching for documentation for product that are available in online shops then I found this one which is listed on Amazon and they have good documentation and for building this kind of project, I think setting up the software with guided would be better
 PDF DOC - https://m.media-amazon.com/images/I/C1yvvKE-JJL.pdf


#### Flashing GRBL onto the Arduino

1. Download the Arduino IDE from their site, a program which allows to flash the Arduino with firmware.
2. Download GRBL source code.zip file from the GitHub repository: https://github.com/gnea/grbl/releases and unzip the grbl file. Before we proceed a we need to modify the config.h file inside grbl to account for the lack of the Z axis.
3. 
![Screenshot 2026-06-23 at 2.59.49 AM](https://stasis.hackclub-assets.com/images/1782163794536-ptjcjs.png)

## Now , 
![Screenshot 2026-06-23 at 3.00.07 AM](https://stasis.hackclub-assets.com/images/1782163811162-tmuz4v.png)

1. Open Arduino IDE and import the grbl file via: Sketch->Include Library->add .zip library.
2. Navigate to the grblUpload sketch via: File -> Examples -> grbl -> grblUpload
3. Connect the Arduino to the laptop via USB (make sure the correct board and port is selected).
4. Flash the sketch through Sketch->Upload

After that we need to connect  the Arduino to LaserGRBL(through which I will control the laser) is simple. First, download LaserGRBL from their website: [https://lasergrbl.com](https://lasergrbl.com) and install it. Then again connect the Arduino to the laptop  via USB, choose the correct port and select "115200" baud rate, then click connect. If the console shows "Grbl 1.1h, the chip is connected.

### Now to configure it correctly go through the doc below : - 
[DOC PDF ](https://lasergrbl.com/wp-content/uploads/2020/05/Grbl-Configuration-ENG.pdf)

 #### Key changes Main

### 1) Configuring Stepper Drivers

**Microstepping Jumpers**

Under each stepper driver socket on the CNC Shield V3 are three jumper pairs (MS1, MS2, MS3). These set the microstepping mode:

| MS1 | MS2 | MS3 | Microstepping (A4988) |
| :---: | :---: | :---: | :---: |
| **OFF** | **OFF** | **OFF** | Full step |
| **ON** | **OFF** | **OFF** | 1/2 step |
| **OFF** | **ON** | **OFF** | 1/4 step |
| **ON** | **ON** | **OFF** | 1/8 step |
| **ON** | **ON** | **ON** | 1/16 step |

Most 3018 CNC routers use 1/8 or 1/16 microstepping. Higher microstepping = smoother motion but lower maximum speed (due to GRBL’s step frequency limit). 1/8 stepping is a good balance.

### Setting Current Limit (VREF)
The most critical stepper driver adjustment is current limit. Over-current burns motors and drivers; under-current causes missed steps. Use a multimeter in DC voltage mode:

Measure VREF between the driver’s trimpot (center of the small adjustable potentiometer) and GND.

1)**For A4988: Imax = VREF / 0.625 (with 0.1Ω sense resistors). Set VREF = (rated motor current × 0.625).**

2)**For DRV8825: Imax = VREF / 0.5. Set VREF = (rated motor current / 2).**

3)**Start at 70–80% of motor rated current. For a 1.7A NEMA17: VREF ≈ 0.85V on A4988.**

### 2) GRBL Settings ($ Parameters)

**Type $$ in your GRBL sender to see all current settings. Here are the most important ones:**

| Parameter | Description | Typical Value (3018) |
| :---: | :--- | :--- |
| **$0** | Step pulse time (µs) | 10 |
| **$1** | Step idle delay (ms) | 25 (255 = always on) |
| **$2** | Step port invert (bitmask) | 0 |
| **$3** | Direction port invert (bitmask) | 0 (adjust if axes move wrong direction) |
| **$4** | Step enable invert | 0 |
| **$5** | Limit pin invert (NC vs NO switches) | 0 (NC=1) |
| **$10** | Status report mask | 1 |
| **$20** | Soft limits enable | 0 (1 if homing enabled) |
| **$21** | Hard limits enable | 0 (1 with limit switches) |
| **$22** | Homing cycle enable | 0 (1 with limit switches) |
| **$100** | X steps/mm | 800 (varies by machine) |
| **$101** | Y steps/mm | 800 |
| **$102** | Z steps/mm | 800 |
| **$110** | X max rate (mm/min) | 800 |
| **$111** | Y max rate (mm/min) | 800 |
| **$112** | Z max rate (mm/min) | 400 (Z is slower) |
| **$120** | X acceleration (mm/s²) | 40 |
| **$130** | X max travel (mm) | 300 (your machine’s X range) |


Change any setting by typing the parameter and value, e.g.: $100=800 followed by Enter. Changes are saved to Arduino EEPROM immediately.


### 3) Calibrating Steps Per mm

**Getting steps/mm right is fundamental — incorrect values mean your G-code dimensions do not match reality. Here is the calculation and calibration process:**

```
Steps/mm = (Motor steps per revolution × Microstepping) / (Lead screw pitch mm)

Example: NEMA17 (200 steps/rev) × 1/8 microstepping / 2mm lead pitch
= 200 × 8 / 2 = 800 steps/mm

For belt drive: replace pitch with (belt pitch × pulley teeth)
Example: GT2 belt, 20-tooth pulley → pitch distance = 2mm × 20 = 40mm/rev
Steps/mm = (200 × 16) / 40 = 80 steps/mm
```

### 4)  Homing Switches and Limit Switches

Homing switches allow GRBL to find a consistent machine origin (machine zero) at power-on. Limit switches prevent the machine from crashing into its mechanical ends. These can be the same switches — GRBL supports both modes.

**Switch Types**
- 1) Normally Closed (NC): Switch is closed (circuit active) when not triggered. Opens when the axis reaches the switch. Safer — a broken wire triggers a fault rather than being invisible.

- 2) Normally Open (NO): Switch is open until triggered. Simpler wiring but a broken wire is invisible to GRBL.

**Wiring Limit Switches**
Each axis minimum switch connects to the Xmin, Ymin, Zmin headers on the CNC shield. Connect one switch terminal to the signal pin and the other to GND. No pull-up resistors are needed — the CNC shield or Arduino provides internal pull-ups on limit inputs.

#### Enabling Homing

```
$22=1   ; Enable homing cycle
$23=0   ; Homing direction mask (0 = home to -X, -Y, +Z)
$24=25  ; Homing feed rate (mm/min) - slow speed for switch contact
$25=500 ; Homing seek rate (mm/min) - fast approach speed
$26=250 ; Homing debounce delay (ms)
$27=1   ; Homing pull-off distance (mm) - backs off switch after homing
$21=1   ; Enable hard limits (optional - halts machine if limit hit)
$20=1   ; Enable soft limits (requires homing to be done first)

```

After enabling homing, type $H to run the homing cycle. The machine will seek each axis minimum (or maximum for Z) at the seek rate, back off, and re-approach slowly for accurate repeatability.

### This are some of the comands that I learn during, searching about the software 


**Key G-code Commands to Know**

```
G28       ; Return to home (machine zero)
G0 X0 Y0  ; Rapid move to work zero (X=0, Y=0)
G1 Z-1 F100  ; Feed move: cut 1mm into material at 100mm/min
G91       ; Set incremental positioning mode
G90       ; Set absolute positioning mode (default)
M3 S1000  ; Spindle on clockwise at 1000 RPM (if spindle is PWM-controlled)
M5        ; Spindle off
```


##  Now for sending the G- Code to the Arduino I will use universal Gcode Sender 

**https://github.com/winder/Universal-G-Code-Sender**

- official website - https://winder.github.io/ugs_website/

- It is an open source software, which is used to control CNC machines to send G code to them and to use it







