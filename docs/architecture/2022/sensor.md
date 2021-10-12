## GNSS

### When using SC-30

```mermaid
flowchart LR
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:5px;
    classDef lowPowerSupply stroke-width:3px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==================

    subgraph GJB["GNSS Junction Box"]
        CON1(["Panel Mount [IP67]<br>NRW-203-RM<br>IN: 24V"]):::lowPowerSupply
        CON2(["Panel Mount RJ-45 [IP67]<br>ROP-5SDFFH-TCU7001"])
        MCB[Mbed Expansion Board]
        IF[SC-30 Interface<br>CAN - Serial Converter]
        CBG1([Cable Ground<br>RM16S-8S ?? ])

        CON1 ==> MCB
        CON2 -.- MCB
        MCB --- IF --- CBG1
    end                        
    GPS["SC-30<br>IN: 12 ~ 24 Vdc 5.5W"]
    
    CBG1 ---|NMEA| GPS
    DUM1[" "]:::dummy === CON1
    DUM2[" "]:::dummy -.- CON2
```

### When using F9P



## IMU

```mermaid
flowchart
                            %% ==== classDef ====
                            classDef highPowerSupply stroke-width:5px;
                            classDef lowPowerSupply stroke-width:3px;
                            classDef commentComponent fill:#0000,stroke:#0000;
                            %% ==================
                            subgraph SENS2[IMU]
                                IMU1["KVH1750<br>IN: 9 ~ 36 Vdc 8W"]
                            end
```


## Optical Sensing

### Perception Array

Waterproof enclosure (WP20-20-7G)<br>Cable glands for cable penetrations
Each element is mounted on a rigid frame.

``` mermaid
flowchart LR
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:5px;
    classDef lowPowerSupply stroke-width:3px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==================
    style PJB stroke-width:4px
    style CAM1 stroke-width:4px
    style CAM2 stroke-width:4px
    %% ==================

    subgraph PJB["Perception Array Junction Box"]
        CON1_PJB(["Panel Mount [IP67]"]):::lowPowerSupply
        CON2_PJB(["Panel Mount RJ-45 [IP67]"])
        CBG1([Cable Ground 1])
        CBG2([Cable Ground 2])
        CBG3([Cable Ground 3])
        CBG4([Cable Ground 4])
        CBG5([Cable Ground 5])
    end
    LDR1["LiDAR<br>VLP-16<br>IN: 9 ~ 18 Vdc 8W"]
    subgraph CAM1["Perception Camera"]
        CON1_CAM1([Power Supply Connector]):::lowPowerSupply
        CON2_CAM1([RJ-45 Connector])
    end
    subgraph CAM2["Perception Camera"]
        CON1_CAM2([Power Supply Connector]):::lowPowerSupply
        CON2_CAM2([RJ-45 Connector])
    end

    CBG1 ---|Power + Ethernet + Sync| LDR1
    CBG2 ==>|24Vdc| CON1_CAM1
    CBG3 -.- CON2_CAM1
    CBG4 ==>|24Vdc| CON1_CAM2
    CBG5 -.- CON2_CAM2

    DUM1[" "]:::dummy === CON1_PJB
    DUM2[" "]:::dummy -.- CON2_PJB
```

#### Perception Array Junction Box


[Circuit Design Documentation](../../circuit_design/perception-array-interface-board.md)

``` mermaid
graph LR
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:5px;
    classDef lowPowerSupply stroke-width:3px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==== style ====
    style PCB stroke-dasharray:5 5
    %% ==================
    
    subgraph ENC["Waterproof enclosure (WP20-20-7G)"]
        CON1(["Panel Mount [IP67]<br>NRW-203-RM<br>IN: 24V"]):::lowPowerSupply
        CON2(["Panel Mount RJ-45 [IP67]<br>ROP-5SDFFH-TCU7001"])
        subgraph PCB["PCB"]
            CON1_PCB([Terminal Block]):::lowPowerSupply
            FS1[FUSE: 3A]:::lowPowerSupply
            FS2[FUSE: 3A]:::lowPowerSupply
            FS3[FUSE: 3A]:::lowPowerSupply
            FS4[FUSE: 3A]:::lowPowerSupply
            CDG1_PCB([Card Edge]):::lowPowerSupply
            CDG2_PCB([Card Edge]):::lowPowerSupply
            DCDC1[DC-DC Conv.<br>OUT: 12V 2A]:::lowPowerSupply
            DCDC2[DC-DC Conv.<br>OUT: 5V 2A]:::lowPowerSupply
            CON2_PCB(["Terminal Block"])
            CON3_PCB([PCB Mount RJ-45])

            CON1_PCB ==> FS1 & FS2 & FS3 & FS4
            FS1 ==> CDG1_PCB
            FS2 ==> CDG2_PCB
            FS3 ==> DCDC1 ====>|12Vdc| CON2_PCB
            FS4 ==> DCDC2
            CON3_PCB -.- CON2_PCB
        end
        PD1[Power Distributor ch1]:::lowPowerSupply
        PD2[Power Distributor ch2]:::lowPowerSupply
        L2SW[5 Port Switching Hub<br>GS305v3<br>IN: 5V 0.7A]
        CBG1([Cable Ground 1<br>RM16S-8S])
        CBG2([Cable Ground 2<br>RM16S-8S])
        CBG3([Cable Ground 3<br>RM16S-8S])
        CBG4([Cable Ground 4<br>RM16S-8S])
        CBG5([Cable Ground 5<br>RM16S-8S])

        CON1 ==>|/3| CON1_PCB
        DCDC2 ==>|5Vdc| L2SW
        CDG1_PCB ====>|24Vdc| PD1 === CBG2
        CDG2_PCB ====>|24Vdc| PD2 === CBG4
        L2SW -.- CON3_PCB
        CON2 -....- L2SW -...- CBG3 & CBG5
        CON2_PCB --- CBG1
    end
    CON3(["Socket/Plug [IP67]<br>NRW-203-PF8<br>OUT: 24Vdc"]):::lowPowerSupply
    CON4(["Socket/Plug [IP67]<br>NRW-203-PF8<br>OUT: 24Vdc"]):::lowPowerSupply
    CON5(["Plug RJ-45 [IP67]<br>ROP-00AMMA-TLM7001"])
    CON6(["Plug RJ-45 [IP67]<br>ROP-00AMMA-TLM7001"])    

    DUM1[" "]:::dummy === CON1
    DUM2[" "]:::dummy -.- CON2
    CBG1 --- DUM3[" "]:::dummy
    CBG2 === CON3
    CBG3 -.- CON5
    CBG4 === CON4
    CBG5 -.- CON6
```


#### Perception Camera

``` mermaid
graph LR
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:5px;
    classDef lowPowerSupply stroke-width:3px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==================
    
    subgraph ENC[Waterproof enclosure]
        CON1(["Panel Mount [IP67]<br>NRW-203-RM<br>IN: 24V"]):::lowPowerSupply
        CON2(["Panel Mount RJ-45 [IP67]<br>ROP-5SDFFH-TCU7001"])
        SW1(Illuminated Switch<br>SPST Momentary<br>LED: Green)
        DCDC1[DC-DC Conv.<br>OUT: 5V 6A]:::lowPowerSupply
        JSN1[Jetson Nano<br>IN: 5V 4A]
        SSD[SSD]
        IMS1["Image Sensor Module<br>IMX219<br>FOV(D): 120deg"]
        PLF1[C-PL Filter]

        CON1 ==>|24Vdc| DCDC1 ==>|5Vdc| JSN1
        CON2 -..- JSN1
        SW1 ---- JSN1
        JSN1 ---|USB| SSD
        JSN1 ---|MIPI CSI-2| IMS1 --- PLF1
    end

    DUM1[" "]:::dummy === CON1
    DUM2[" "]:::dummy -.- CON2
```

### Side Perception Array

```mermaid
flowchart
                        %% ==== classDef ====
                        classDef highPowerSupply stroke-width:5px;
                        classDef lowPowerSupply stroke-width:3px;
                        classDef commentComponent fill:#0000,stroke:#0000;
                        %% ==================
                        subgraph PA3[Side Perception Array]
                            subgraph PAS1["SidePerception Array Sensor"]
                                subgraph "/* Comment */"
                                    COM_PAS1["Each element is mounted on a rigid frame."]:::commentComponent
                                end
                                LDR3[Livox MID-70]
                                subgraph CAM11["Perception Camera"]
                                    CON1_CAM11([NRW-207-RM<br>IN: 24V]):::lowPowerSupply
                                    CON2_CAM11([RJ-45 Connector<br>ROP-5SDFFH-TCU7001])
                                end
                            end
                        end
```


## Underwater Acoustic

```mermaid
flowchart
                            %% ==== classDef ====
                            classDef highPowerSupply stroke-width:5px;
                            classDef lowPowerSupply stroke-width:3px;
                            classDef commentComponent fill:#0000,stroke:#0000;
                            %% ==================
                            subgraph UAS[Underwater Acoustic]
                                subgraph UACB["Underwater Acoustic Control Box (Waterproof Box)"]
                                    CON1_UACB>NRW-207-RM<br>IN: 24Vdc]
                                    CON2_UACB>RJ-45 Connector<br>ENRW-28SC5E-R]
                                    DCDC1_UACB[DC-DC Conv.<br>OUT: 5Vdc 6A]
                                    MC1_UACB[mbed]
                                    ADC_UABC[Mic PreAmp + ADC]
                                    CON1_UACB ==> DCDC1_UACB ==> MC1_UACB
                                    CON2_UACB -..- MC1_UACB
                                    MC1_UACB --- ADC_UABC
                                end
                                subgraph MCA[Mic Array]
                                    MIC1[Underwater Mic ch1]
                                    MIC2[Underwater Mic ch2]
                                    MIC3[Underwater Mic ch3]
                                end
                                ADC_UABC --- MIC1 & MIC2 & MIC3
                            end
```


## Anemometer
``` mermaid
flowchart
                            %% ==== classDef ====
                            classDef highPowerSupply stroke-width:5px;
                            classDef lowPowerSupply stroke-width:3px;
                            classDef commentComponent fill:#0000,stroke:#0000;
                            %% ==================
                            subgraph ANM1[Anemometer]
                                CON1_ANM1>NRW-207-RM<br>IN: 24Vdc]
                                CON2_ANM1>RJ-45 Connector<br>ENRW-28SC5E-R]
                                DCDC1_ANM1[DC-DC Conv.<br>OUT: 5Vdc 6A]
                                MC1_ANM1[mbed]
                            end
```

