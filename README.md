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
It's an hobby grade laser engraver that I have made the model in fusion 360 and after that, I have specifically selected the components that fits the budget and it is easily modified and it can be later upgraded into something related to CNC. And this is an open source project.

### Why I chose this project?
I chose to build a CNC laser engraver because it combines both the hardware and the software and while making it I have learnt a lot about CAD design how to take dimension from data sheet and implemented in CAD also learned about how XY coordinate works in an CNC

### How to use this project
This can be used in various ways for me. I will use it to engrave in small MDF board for my projects, and I can also cut small things with it like if I want to make an keyboard, I can cut out the base plate for the keyboard with it with extreme accuracy and it will enhance the project quality. Also, it can be used in other way too.

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
  <img width="962" height="361" alt="44" src="https://github.com/user-attachments/assets/49d852d6-a136-48ff-9333-d32abe83b05f" style="border: 2px solid #ccc; border-radius: 4px; padding: 4px;" />
</p>

## Setup -  [setup.md](https://github.com/Sadrita404/Robo-Laser/blob/main/setup.md)

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

##  Now for sending the G- Code to the Arduino I will use universal Gcode Sender 

**https://github.com/winder/Universal-G-Code-Sender**

- official website - https://winder.github.io/ugs_website/

- It is an open source software, which is used to control CNC machines to send G code to them and to use it



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


<div align="center">
  <h2> Bill of Materials</h2>
</div>

| Component Name | Purpose | Qty | Total Price | Source Link | Distributor |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **1W Laser Engraver with adjustable Focus** | Laser cutting/engraving tool | 1 | $61.31 | [roboticsdna](https://roboticsdna.in/product/1w-laser-engraver-with-adjustable-focus/?src=google&kwd=&adgroup={adgroup}&device=c&campaign={campaign}&adgroup={adgroup}&keyword=&matchtype=&gad_source=1&gad_campaignid=22411741198&gbraid=0AAAAAC-xzeEHQaOHm_kbuCpTwq_3kptRY&gclid=CjwKCAjwuuPRBhAnEiwA2Ji8ev-95CF4b0_I65wOQ50L94g51sJtA9l6bnxksraq3EbTCGYeRxS31BoColYQAvD_BwE) | roboticsdna |
| **M5 Hex Nut** | General assembly fastening | 20 | $0.17 | [OnlyScrews](https://onlyscrews.in/products/m5-hex-nut-mild-steel-grey-dia-5mm?currency=INR&country=IN&variant=50254623572281&stkn=6e84ebfba1b8&utm_source=google&utm_medium=cpc&utm_campaign=inderans_campaign_copy&gad_source=1&gad_campaignid=22930701107&gbraid=0AAAAA9sP2SRMlcD-Z6w_Ac7lrMRiHrOE9&gclid=CjwKCAjw9NjRBhATEiwA_p2J8XKFV51W0pwLAg9wZ5tcxzuN4MJaB3KOhltnwSGSkhATwiSfKsI8-BoC4fIQAvD_BwE) | onlyscrews |
| **M5 x 10mm** | Extrusion/bracket fastening | 20 | $0.51 | [OnlyScrews](https://onlyscrews.in/products/m5-x-10mm-hex-allen-button-head-high-tensile10-9-black-oxide-screw-dia-5mm-length-10mm?currency=INR&country=IN&variant=50000663609657&stkn=6e84ebfba1b8&utm_source=google&utm_medium=cpc&utm_campaign=inderans_campaign_copy&gad_source=1&gad_campaignid=22930701107&gbraid=0AAAAA9sP2SRMlcD-Z6w_Ac7lrMRiHrOE9&gclid=CjwKCAjw9NjRBhATEiwA_p2J8daedFNuW-ZBlH9jloPm-Lv_WfGEfT840zK7bPX-lEQJjBWSi9l8LhoC9tsQAvD_BwE) | onlyscrews |
| **M3 X 8mm Hex** | Motor/shield component mounting | 20 | $0.55 | [OnlyScrews](https://onlyscrews.in/products/m3-x-8mm-hex-allen-button-head-hight-tensile10-9-black-oxide-screw-dia-3mm-length-8mm?currency=INR&country=IN&variant=49994660217145&stkn=6e84ebfba1b8&utm_source=google&utm_medium=cpc&utm_campaign=inderans_campaign_copy&gad_source=1&gad_campaignid=22930701107&gbraid=0AAAAA9sP2SRMlcD-Z6w_Ac7lrMRiHrOE9&gclid=CjwKCAjw9NjRBhATEiwA_p2J8ZsNPlGBt6jLRl-JZ1BSu_mu_AslKdOORhMDUSLztgSyqRHB3XoJABoC9ZcQAvD_BwE) | onlyscrews |
| **M5 X 35mm Hex** | Gantry/structural fastening | 20 | $0.76 | [OnlyScrews](https://onlyscrews.in/products/m5-x-35mm-hex-allen-button-head-high-tensile10-9-black-oxide-screw-dia-5mm-length-35mm?currency=INR&country=IN&variant=51471379202361&stkn=6e84ebfba1b8&utm_source=google&utm_medium=cpc&utm_campaign=inderans_campaign_copy&gad_source=1&gad_campaignid=22930701107&gbraid=0AAAAA9sP2SRMlcD-Z6w_Ac7lrMRiHrOE9&gclid=CjwKCAjw9NjRBhATEiwA_p2J8Qp1l36Ras0sQy98Yvg_fh_E_CYTRqM2LjnSrmfJVEuity6T8y3ukhoCS9sQAvD_BwE) | onlyscrews |
| **A4988 Driver Stepper Motor Driver** | Stepper motor control interface | 4 | $2.54 | [FlyRobo](https://www.flyrobo.in/a4988-driver-stepper-motor-driver?tracking=ads&tracking=4a9a9a&gad_source=1&gad_campaignid=17426303996&gbraid=0AAAAAC6AkE8OP6QxygQu1YgTfEHvuoXvM&gclid=CjwKCAjw9NjRBhATEiwA_p2J8ScTH6S7N2wP4FKytFsUi9vNBD2d2CAncAOqp5txiIcRBEdQ-ktRcxoCTR0QAvD_BwE) | flyrobo |
| **Allen Key** | 	To fix the Rails | 1 | $2.11 | [onlyscrews](https://onlyscrews.in/products/allen-key-mm-set-m1-5-to-m10-chrome-vanadium-steel?variant=49975496671545) | amazon |
| **5 mm Tap set** | 		To make holes in the Extrusion Rod | 1 | $5.60 | [amazon](https://www.amazon.in/gp/product/B0D1R57NP7/ref=ox_sc_act_title_1?smid=A1ONML66JO9EQE&psc=1) | onlyscrews |
| **T-Slot inside corner connector for 2020** | Rigid frame joint support | 1 | $2.82 | [Robu](https://robu.in/product/easymech-2020-series-corner-slot-connector/?) | Robu |
| **Mech Endstop Switch** | Axis limit/homing switches | 8 | $3.99 | [Robu](https://robu.in/product/cnc-3d-printer-mech-endstop-switch/?gad_source=1&gad_campaignid=17427803012&gbraid=0AAAAADvLFWdPrAljERasEupxxQ-c5ODyD&gclid=CjwKCAjw9NjRBhATEiwA_p2J8SLSkMkZHy74gMLexfRQJBnWJkSaAeeu3UOZ6gsi7xmL5p16lEXBMhoCCPQQAvD_BwE) | robu |
| **T-Slot inside corner connector for 2020** | Rigid frame joint support | 1 | $2.82 | [Robu](https://robu.in/product/easymech-2020-series-corner-slot-connector/?gad_source=1&gad_campaignid=17427803012&gbraid=0AAAAADvLFWdPrAljERasEupxxQ-c5ODyD&gclid=CjwKCAjw9NjRBhATEiwA_p2J8XW-fTa0nV1ypFiHTs-TXZnSegw8YiXpIqy1tqriI7vKKrFy8Yr2PxoCC0wQAvD_BwE) | robu |
| **NEMA 17 Stepper Motor, Bipolar, 1.5A** | Axis motion actuation | 3 | $22.79 | [Robu](https://robu.in/product/nema17-pr42hs40-1204af-02-4-2kg-cm-stepper-motor-d-type-shaft/?gad_source=1&gad_campaignid=20381096599&gbraid=0AAAAADvLFWfhrgZve0DQQvDwygXEO2tsk&gclid=CjwKCAjw9NjRBhATEiwA_p2J8VUlspMYRNcnTDpOZkIBuRVf425s31KE2AbK-_Ti7KOK4nw-1LPKwhoC9xkQAvD_BwE) | robu |
| **arduino uno r3 board** | Stepper motor control interface | 1 | $2.28 | [Robu](https://robu.in/product/arduino-uno-r3-ch340g-atmega328p-devlopment-board/?gad_source=1&gad_campaignid=17413441824&gbraid=0AAAAADvLFWcYEvmIsduRBCOcZBvQhM4xX&gclid=CjwKCAjw9NjRBhATEiwA_p2J8febOyavNr48NQoOi1VdQRHro2eYIQAsIcv4rHK8I3Gnkk7i_THhmhoC8DsQAvD_BwE) | robu |
| **CNC Shield V3** | Stepper motor control interface | 1 | $1.48 | [FlyRobo](https://www.flyrobo.in/cnc-shield-v3-for-engraving-machine-3d-printer-a4988-drv8825-driver-expansion-board?tracking=ads&tracking=4a9a9a&gad_source=1&gad_campaignid=17426303996&gbraid=0AAAAAC6AkE8OP6QxygQu1YgTfEHvuoXvM&gclid=CjwKCAjw9NjRBhATEiwA_p2J8e9AHPcF3RQdr6UOsqpr_OcnySgFo0Gja_ifPGLrct4SHcUx0DGCWBoCTQ0QAvD_BwE) | flyrobo |
| **V Slot gantry wheel(625zz)** | Gantry linear movement | 14 | $8.46 | [FlyRobo](https://www.flyrobo.in/openbuilds-plastic-wheel-idler-pulley?tracking=ads&tracking=4a9a9a&gad_source=1&gad_campaignid=17426303996&gbraid=0AAAAAC6AkE8OP6QxygQu1YgTfEHvuoXvM&gclid=CjwKCAjw9NjRBhATEiwA_p2J8QGTEEEIZ1dfv8KfgR0Ng49gtRanAmdukoyFnAkNJ0cECkEtEJm02RoCes4QAvD_BwE) | flyrobo |
| **GT2 Timing Belt, 5M, 6mm width** | Linear motion drive | 1 | $4.66 | [Robu](https://robu.in/product/5-meter-x-gt2-open-timing-belt-6mm-width/?gad_source=1&gad_campaignid=17427803012&gbraid=0AAAAADvLFWdPrAljERasEupxxQ-c5ODyD&gclid=CjwKCAjw9NjRBhATEiwA_p2J8W8TiT7rVNSo_hMI0i0-3jGSWh_hCjVlUf_nrh0P6dQweNCfycJ0HhoCdFYQAvD_BwE) | robu |
| **2040 Aluminum Extrusion, 1000mm V Slot** | Main structural frame | 5 | $62.55 | [Robu](https://robu.in/product/easymech-1000-mm-20x40-4-v-slot-aluminium-extrusion-profile-black/) | robu |
| **20 Tooth 5mm Bore GT2 Timing Pulley** | Belt drive transmission | 6 | $2.09 | [FlyRobo](https://www.flyrobo.in/20-teeth-5mm-bore-gt2-black-timing-pulley-for-6mm-belt?tracking=ads&tracking=4a9a9a&gad_source=1&gad_campaignid=17426303996&gbraid=0AAAAAC6AkE8OP6QxygQu1YgTfEHvuoXvM&gclid=CjwKCAjw9NjRBhATEiwA_p2J8SdUwhJo0U_wVIlUSlG2aQ3nyiUvAJBt9r7wMYWKXMdBElK04fNV0hoCOnQQAvD_BwE) | flyrobo |
| **M5 X 100mm Hex** | Structural fastening | 1 | $0.34 | [link](https://3fparts.com/shop/m5-100mm-hex-bolt-din-933-stainless-steel-304-a2-70?srsltid=AfmBOopubs1oxz9r71rdxJmCbhOA09e2XBk-N5C1WeqYFXRF0YHUMZgXnbU) | Self - Sourced |
| **M4 X 100mm Hex** | Structural fastening | 2 | $0.89 | [OnlyScrews](https://onlyscrews.in/products/m4-x-100mm-hex-allen-socket-head-ss-304-screw-dia-4mm-length-100mm?currency=INR&country=IN&variant=50100898300217&stkn=6e84ebfba1b8&utm_campaign=sales_shopping_pfmax&gad_source=1&gad_campaignid=23146719598&gbraid=0AAAAA9sP2SSl4HgRihEwJBpJCj_UuavSl&gclid=CjwKCAjw9NjRBhATEiwA_p2J8U33y_23aXj6qecYVRSgVZABI_5vMMizr8iKm5fYs_kAK3pIwPY_uBoC0hUQAvD_BwE) | onlyscrews |
| **M5 Profile Nuts** | Frame assembly hardware | 20 | $1.90 | [OnlyScrews](https://onlyscrews.in/products/m4-profile-nuts-mild-steel-with-nickel-plating-for-3030-series-t-nut-hammer-nut-1) | onlyscrews |
| **M4 Profile Nuts** | Frame assembly hardware | 20 | $1.84 | [OnlyScrews](https://onlyscrews.in/products/m4-profile-nuts-mild-steel-with-nickel-plating-for-2020-series-t-nut-hammer-nut) | onlyscrews |
| **M3 Profile Nuts** | Frame assembly hardware | 20 | $1.80 | [OnlyScrews](https://onlyscrews.in/products/m3-profile-nuts-mild-steel-with-nickel-plating-for-2020-series-t-nut-hammer-nut) | onlyscrews |
| **Cable with Connector for NEMA17 Motor** | Motor connection | 4 | $1.90 | [Robu](https://robu.in/product/pure-copper-1000-mm-cable-with-connector-for-nema17-stepper-motor/?gad_source=1&gad_campaignid=20381096599&gbraid=0AAAAADvLFWdRG0rCC-w9yrGhKwdtsxu3w&gclid=CjwKCAjwuuPRBhAnEiwA2Ji8euXbJ3ClnqKgJD--M4510dq9MZgBy_y_kccCa_0XEcVQSvi95V8pAxoCj5UQAvD_BwE) | robu |


<div align="center">
  <table border="0" cellpadding="0" cellspacing="0" style="border-collapse: collapse; max-width: 600px;">
    <tr>
      <td style="background: #ffffff; border: 1px solid #d0d7de; border-radius: 12px; padding: 20px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif;">
        <div style="font-size: 16px; font-weight: 600; color: #24292f; margin-bottom: 12px; border-bottom: 1px solid #d0d7de; padding-bottom: 8px;">
          Final Bill
        </div>
        <table width="100%" border="0" style="border-collapse: collapse; font-size: 14px; color: #57606a;">
          <tr>
            <td style="padding: 4px 0;">Component Subtotal:</td>
            <td align="right" style="font-weight: 500; color: #24292f;">$193</td>
          </tr>
          <tr>
            <td style="padding: 4px 0;"> Shipping:</td>
            <td align="right" style="font-weight: 500; color: #24292f;">$5.3</td>
          </tr>
          <tr>
            <td style="padding: 4px 0; padding-bottom: 8px;"> Tax:</td>
            <td align="right" style="font-weight: 500; color: #24292f;">$1.1</td>
          </tr>
          <tr style="border-top: 1px dashed #d0d7de;">
            <td style="padding: 12px 0 0 0; font-weight: 600; color: #24292f; font-size: 15px;">Net Total Cost:</td>
            <td align="right" style="padding: 12px 0 0 0; font-weight: bold; color: #2da44e; font-size: 18px;">$199.40</td>
          </tr>
          <tr>
            <td style="padding: 2px 0 0 0; font-size: 11px; color: #8c959f;">Projected Budget Allocation:</td>
            <td align="right" style="padding: 2px 0 0 0; font-weight: 500; font-size: 12px; color: #8c959f;">$200</td>
          </tr>
        </table>
      </td>
    </tr>
  </table>
</div>

**Project Under Hack Club**
I have provided the links to the parts that I will self - sourced , So that if a reader wanted to recreate this project they would be able to find all the parts..


