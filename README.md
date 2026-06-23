  <table border="0" cellpadding="0" cellspacing="0">
    <tr>
      <td align="center" style="background: #ffffff; border: 1px solid #d0d7de; border-radius: 12px; padding: 16px; box-shadow: 0 4px 12px rgba(0,0,0,0.05);">
        <img src="https://github.com/user-attachments/assets/22cf5526-fe91-46e3-a834-389a0b7172fd" width="100%" max-width="800px" alt="Rough Layout For The PCB" style="border-radius: 6px;" />
        <div style="margin-top: 12px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif; font-size: 13px; color: #57606a; font-weight: 500;">
      </td>
    </tr>
  </table>
</div>



|Title | Robo Laser |
|:-- |:--|
|Author | Sadrita Neogi|



## Overview


---

<div align="center">
  <table border="0" cellpadding="0" cellspacing="0">
    <tr>
      <td align="center" style="background: #ffffff; border: 1px solid #d0d7de; border-radius: 12px; padding: 16px; box-shadow: 0 4px 12px rgba(0,0,0,0.05);">
        <img src="https://github.com/user-attachments/assets/9d0a25de-b5b8-469f-a426-b0af763ceba2" width="100%" max-width="800px" alt="Rough Layout For The PCB" style="border-radius: 6px;" />
        <div style="margin-top: 12px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif; font-size: 13px; color: #57606a; font-weight: 500;">
      </td>
    </tr>
  </table>
</div>

|  | CAD WORK   |  |  
| :-: | :-: | :-: | 
| <img src="https://github.com/user-attachments/assets/aee79869-c008-4d35-bb09-496195e24699" width="250" alt="Full Board Layout" style="border-radius: 12px;" /> | <img src="https://github.com/user-attachments/assets/a397e43d-7e2c-441f-9e14-77fd03487956" width="250" alt="Component Placement" style="border-radius: 12px;" /> | <img src="https://github.com/user-attachments/assets/03881715-6ba4-4c24-a418-abbaf1c9e2e8" width="250" alt="Connection Map" style="border-radius: 12px;" /> |
| <img src="https://github.com/user-attachments/assets/a8abb20d-c34a-4d63-a4c3-916a181152fa" width="250" alt="Trace Routing Detail" style="border-radius: 12px;" /> | <img src="https://github.com/user-attachments/assets/fb6028a5-c25d-4f8d-806a-33b1f1d34965" width="250" alt="Alternate Connection Map" style="border-radius: 12px;" /> | <img src="https://github.com/user-attachments/assets/a63d7874-3cc8-44ff-8b16-aac27b43ac38" width="250" alt="Secondary Trace Detail" style="border-radius: 12px;" /> |
| <img src="https://github.com/user-attachments/assets/ba4bd52d-7ed5-4505-972e-387d4f3f70a0" width="250" alt="Component Placement 2" style="border-radius: 12px;" /> | <img src="https://github.com/user-attachments/assets/54fbd067-7314-4613-a1f7-c0772bdbcfb3" width="250" alt="Routing Detail 3" style="border-radius: 12px;" /> | <img src="https://github.com/user-attachments/assets/753dbfae-2236-4067-b380-ab24387536f3" width="250" alt="Routing Detail 4" style="border-radius: 12px;" /> |
| <img src="https://github.com/user-attachments/assets/caec9c6c-30c8-45eb-b274-620e789831e2" width="250" alt="Routing Detail 5" style="border-radius: 12px;" /> | <img src="https://github.com/user-attachments/assets/c1449627-3c25-4e95-927f-2b95c318d60a" width="250" alt="Routing Detail 6" style="border-radius: 12px;" /> | <img src="https://github.com/user-attachments/assets/82a9bf1b-4692-4ba7-b871-a9fa6b89c73b" width="250" alt="Final Routing Detail" style="border-radius: 12px;" /> |

---
## Wiring Diagram 

<p align="center">
  <img width="618" height="407" alt="44" src="https://github.com/user-attachments/assets/e32603db-b241-4240-99d3-a32c2ae15fff" style="border: 2px solid #ccc; border-radius: 4px; padding: 4px;" />
</p>

## Setup

Once the machine is assembled and wired, firmware needs to be installed so that it can move.

### Flashing GRBL onto the Arduino
GRBL is the firmware which is going to run on the Arduino and interpret the G-code commands. The installation is fairly simple.

1. **Download the Arduino IDE** from their site, a program which allows to flash the Arduino with firmware.
2. **Download GRBL source code** `.zip` file from the GitHub repository: https://github.com/gnea/grbl/releases and unzip the grbl file. 
   > **Note:** Before we proceed, we need to modify the `config.h` file inside grbl to account for the lack of the Z axis.
3. **Open Arduino IDE and import the grbl file** via: `Sketch` -> `Include Library` -> `Add .ZIP Library...` *(it says .ZIP but the uncompressed file should be chosen)*.
4. **Navigate to the grblUpload sketch** via: `File` -> `Examples` -> `grbl` -> `grblUpload`.
5. **Connect the Arduino to the PC via USB** *(make sure the correct board and port is selected)*.
6. **Flash the sketch** through `Sketch` -> `Upload`.

---

### Connecting the Arduino to LaserGRBL
Connecting the Arduino to LaserGRBL (through which I will control the laser) is fairly simple.

1. **Download LaserGRBL** from their website: https://lasergrbl.com and install it.
2. **Connect the Arduino to the computer via USB**.
3. **Choose the correct port** and select **"115200" baud rate**, then click **Connect**. 

If the console shows `Grbl 1.1h`, the chip is connected.

---
<div align="center">
  <h2> Final Look After Render </h2>
</div>

<p align="center">
  <img width="618" height="407" alt="44" src="https://github.com/user-attachments/assets/224986db-679b-41e3-a770-2fdd25e1143d" style="border: 2px solid #ccc; border-radius: 4px; padding: 4px;" />
</p>

<p align="center">
  <img width="624" height="384" alt="45" src="https://github.com/user-attachments/assets/13ac9ddf-158d-469f-80b2-c751fa957b52" style="border: 2px solid #ccc; border-radius: 4px; padding: 4px;" />
</p>

<p align="center">
  <img width="517" height="403" alt="46" src="https://github.com/user-attachments/assets/18cd300b-f646-444a-836f-9a9d9d5cbf93" style="border: 2px solid #ccc; border-radius: 4px; padding: 4px;" />
</p>

<p align="center">
  <img width="605" height="470" alt="47" src="https://github.com/user-attachments/assets/a0275abf-d32b-49ee-88fe-8273d06a60d3" style="border: 2px solid #ccc; border-radius: 4px; padding: 4px;" />
</p>

