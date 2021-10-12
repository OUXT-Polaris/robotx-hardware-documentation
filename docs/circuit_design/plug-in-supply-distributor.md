## Design files

We use KiCAD for PCB design. The CAD data is available in the repository shown in the table below.

| Repository name | Link |
| --- | --- |
| plug-in-supply-distributor | [<i class="fab fa-github"></i> Github](https://github.com/OUXT-Polaris/plug-in-supply-distributor){:target="_blank"} |

## PCB Rendering images

<div style="text-align:center">
  <figure style="display:inline-block;margin-right:25px">
    <img width="400" src="https://github.com/OUXT-Polaris/plug-in-supply-distributor/blob/main/images/pcb_image_topview.png?raw=true" />
    <figcaption style="caption-side:bottom;text-align:center;font-weight:bold;color:navy">Top view</figcaption>
  </figure>
  <figure style="display:inline-block;margin-left:25px">
    <img width="400" src="https://github.com/OUXT-Polaris/plug-in-supply-distributor/blob/main/images/pcb_image_bottomview.png?raw=true" />
    <figcaption style="caption-side:bottom;text-align:center;font-weight:bold;color:navy">Bottom view</figcaption>
  </figure>
</div>

## Photos

## Features

- Provides connector interlock

## Specifications

### Maximum Ratings

| Parameter | Conditions | Min. | Typ. | Max. | Unit |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |

### Schematics

<figure>
  <img width="1000" src="https://github.com/OUXT-Polaris/plug-in-supply-distributor/blob/main/images/schematics.png?raw=true" />
  <figcaption style="caption-side:bottom;text-align:center;font-weight:bold;color:navy">Schematics 1/1</figcaption>
</figure>

### Connectors Pin Assign

#### J1


#### J2

| Pin # | Pin Name | Type/Dir | Description |
| --- | --- | --- | --- |
| 1 | GND | Ground | Connects to LED cathode to indicate the input of the power supply is valid. |
| 2 |  | Output | Connects to LED anode to indicate the input of the power supply is valid. |
| 3 | GND | Ground |  |
| 4 |  | Input | Open Pin 3 and Pin 4 to disable the power supply from VOUT pin. |
| 5 | GND | Ground | Connects to LED cathode to indicate the power is being supplied from VOUT pin. |
| 6 |  | Output | Connects to LED anode to indicate the power is being supplied from VOUT pin. |

#### J3

| Pin # | Pin Name | Type/Dir | Description |
| --- | --- | --- | --- |
| 1 | VOUT | Power | Power supply |

#### J4

| Pin # | Pin Name | Type/Dir | Description |
| --- | --- | --- | --- |
| 1 | IL | Input | If this pin is not connected to the ground level, the power supply from the VOUT pin is stopped. |

#### J5

| Pin # | Pin Name | Type/Dir | Description |
| --- | --- | --- | --- |
| 1 | GND | Ground |  |

### BOM