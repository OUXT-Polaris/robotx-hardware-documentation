## Design files

We use KiCAD for PCB design. The CAD data is available in the repository shown in the table below.

| Repository name | Link |
| --- | --- |
| perception-array-interface-board | [<i class="fab fa-github"></i> Github](https://github.com/OUXT-Polaris/perception-array-interface-board){:target="_blank"} |

## PCB Rendering images

<div style="text-align:center">
  <figure style="display:inline-block;margin-right:25px">
    <img width="400" src="https://github.com/OUXT-Polaris/perception-array-interface-board/blob/main/images/pcb_image_topview.png?raw=true" />
    <figcaption style="caption-side:bottom;text-align:center;font-weight:bold;color:navy">Top view</figcaption>
  </figure>
  <figure style="display:inline-block;margin-left:25px">
    <img width="400" src="https://github.com/OUXT-Polaris/perception-array-interface-board/blob/main/images/pcb_image_bottomview.png?raw=true" />
    <figcaption style="caption-side:bottom;text-align:center;font-weight:bold;color:navy">Bottom view</figcaption>
  </figure>
</div>

## Photos

<figure>
    <img width="400" src="PXL_20210809_143638858_2.jpg" />
    <figcaption style="caption-side:bottom;text-align:center;font-weight:bold;color:navy">Appearance of first prototype</figcaption>
</figure>

## Features

- Serves as a simple interface box for the velodyne lidar (VLP-16).
- Power supply to switching hub.
- Power supply to the Perception Camera.


## Specifications

### Maximum Ratings

| Parameter | Conditions | Min. | Typ. | Max. | Unit |
| --- | --- | --- | --- | --- | --- |
| Input voltage |  | 16 | 24 | 30 | Vdc |

### Schematics

<figure>
  <img width="1000" src="https://github.com/OUXT-Polaris/perception-array-interface-board/blob/main/images/schematics.png?raw=true" />
  <figcaption style="caption-side:bottom;text-align:center;font-weight:bold;color:navy">Schematics 1/1</figcaption>
</figure>

### BOM

| Reference | Value | Footprint | Datasheet |
| --- | --- | --- | --- |
| C1 C2 C3 C4 | 10u 35V | Capacitor_SMD:C_0805_2012Metric_Pad1.18x1.45mm_HandSolder | ~ |
| C5 | 22u 10V | Capacitor_SMD:C_1206_3216Metric_Pad1.42x1.75mm_HandSolder | ~ |
| C6 | 22u 25V | Capacitor_SMD:C_1206_3216Metric_Pad1.42x1.75mm_HandSolder | ~ |
| D1 D2 | 5KP30A-E3/54 | Diode_THT:D_P600_R-6_P7.62mm_Vertical_KathodeUp | https://www.vishay.com/docs/88308/88308.pdf |
| F1 F2 F3 F4 | Mini Blade Fuse 32V 3A | Fuse:RSPRO_1884617_plus_fuse | https://docs.rs-online.com/92e6/A700000006779340.pdf |
| H1 H2 H3 H4 H5 H6 | MountingHole | MountingHole:MountingHole_2.7mm_M2.5 | ~ |
| J1 J2 | PV-3 | Terminal:PV-3 | https://www.mac8sdk.co.jp/uploads/entry_meta/file_value/1597/mac8_2018a_jp-pv-3-4.pdf |
| J3 | PV-3 | Terminal:PV-3_via | https://www.mac8sdk.co.jp/uploads/entry_meta/file_value/1597/mac8_2018a_jp-pv-3-4.pdf |
| J4 J5 | 2-5530843-7 | Connector:TE-Connectivity_2-5530843-7 | https://www.te.com/usa-en/product-2-5530843-7.html |
| J6 | Conn_01x02 | Connector_PinHeader_2.54mm:PinHeader_1x02_P2.54mm_Vertical | ~|
| J7 | RJHSE5381 | Connector_RJ:RJ45_Amphenol_RJHSE538X | https://www.amphenol-icc.com/modular-jacks-rjhse5381.html |
| J8 | 1715789 | TerminalBlock_Phoenix:TerminalBlock_Phoenix_MKDS-1,5-8-5.08_1x08_P5.08mm_Horizontal | https://www.phoenixcontact.com/online/portal/us?uri=pxc-oc-itemdetail:pid=1715789&library=usen&tab=1 |
| R1 | 1k | Resistor_SMD:R_0603_1608Metric_Pad1.05x0.95mm_HandSolder | ~ |
| U1 | K7805-2000R3 | SuperRegulator:RSPRO_K78xx-2000R3 | https://docs.rs-online.com/fc3c/A700000006631878.pdf |
| U2 | K7812-2000R3L | SuperRegulator:RSPRO_K78xx-2000R3L | https://docs.rs-online.com/fc3c/A700000006631878.pdf |
