## Actuator

``` mermaid
flowchart
                        %% ==== classDef ====
                            classDef highPowerSupply stroke-width:5px;
                            classDef lowPowerSupply stroke-width:3px;
                        %% ==================
                            subgraph AZT1[Azimuth Thruster]
                                subgraph AZD1["Azimuth Thruster Driver (Waterproof Box)"]
                                    CON1_AZD1([?????<br>IN: 24Vdc]):::highPowerSupply
                                    CON2_AZD1([NRW-207-RM<br>IN: 24Vdc]):::lowPowerSupply
                                    CON3_AZD1([RJ-45 Connector<br>ENRW-28SC5E-R])
                                    CON4_AZD1([RJ-45 Connector<br>ENRW-28SC5E-R])
                                    DCDC1_AZD1[DC-DC Conv.<br>OUT: 5Vdc 6A]:::lowPowerSupply
                                    subgraph MD1["Brushed DC Motor Driver (PCB)"]
                                        HB_MD1["(opt-isolated input)<br>Gate Driver + H-Bridge<br>IN: 24Vdc"]:::highPowerSupply
                                        MC1_MD1[mbed]

                                        MC1_MD1 -->|PWM| HB_MD1
                                    end
                                    DCDC2_AZD1[Isolated DC-DC Conv.<br>OUT: 12Vdc]:::highPowerSupply
                                    subgraph DC1["Dynamixel Converter (PCB)"]
                                        MC1_DC1[mbed]
                                    end

                                    CON1_AZD1 ==>|24Vdc| HB_MD1
                                    CON1_AZD1 ====>|24Vdc| DCDC2_AZD1
                                    CON2_AZD1 ==>|24Vdc| DCDC1_AZD1
                                    DCDC1_AZD1 ==>|5Vdc| MC1_MD1 & MC1_DC1
                                    CON3_AZD1 -..- MC1_MD1
                                    CON4_AZD1 -...- MC1_DC1
                                end
                                subgraph Azimuth Thruster
                                    subgraph EOM1[Electric Outboard Motor]
                                        BDC_AZT1[LACOMETA 86<br>IN: 24V 48Amax]:::highPowerSupply
                                    end
                                    subgraph ARM1[Azimuth Axis Rotation Motor]
                                        SM1_ARM1[Dynamixel XM540-W270<br>IN: 12Vdc]:::highPowerSupply
                                    end
                                end

                                HB_MD1 ==>|24V PWM| BDC_AZT1
                                DCDC2_AZD1 ==>|12Vdc| SM1_ARM1
                                MC1_DC1 ---|RS-485 or TTL| SM1_ARM1
                            end
```


``` mermaid
flowchart
                        %% ==== classDef ====
                            classDef highPowerSupply stroke-width:5px;
                            classDef lowPowerSupply stroke-width:3px;
                            classDef commentComponent fill:#0000,stroke:#0000;
                        %% ==================
                            subgraph BL1[Ball Launcher]
                                subgraph BLCB["Ball Launcher Control Box (Waterproof Box)"]
                                    CON1_BLCB>NRW-207-RM<br>IN: 24Vdc]
                                    CON2_BLCB>RJ-45 Connector<br>ENRW-28SC5E-R]
                                    DCDC1_BLCB[DC-DC Conv.<br>OUT: 5Vdc 6A]
                                    MC1_BLCB[mbed]

                                    CON1_BLCB ==> DCDC1_BLCB
                                    DCDC1_BLCB ==> MC1_BLCB
                                    CON2_BLCB -..- MC1_BLCB
                                end
                                subgraph BLT["Ball Launcher Turret"]
                                    SM1_BLT[waterproof servo motor]
                                    SM2_BLT[waterproof servo motor]
                                    SM3_BLT[waterproof servo motor]
                                    XXX_BLT[LIDAR or REALSENSE]
                                end
                                MC1_BLCB --- SM1_BLT & SM2_BLT & SM3_BLT
                            end
```
