## Indicator

``` mermaid
flowchart
                        %% ==== classDef ====
                            classDef highPowerSupply stroke-width:5px;
                            classDef lowPowerSupply stroke-width:3px;
                            classDef commentComponent fill:#0000,stroke:#0000;
                        %% ==================
                            subgraph SIDC[State Indicator]
                                subgraph SICB["State Indicator Control Box (Waterproof Box)"]
                                    CON1_SICB>NRW-207-RM<br>IN: 24V]
                                    CON2_SICB>RJ-45 Connector<br>ENRW-28SC5E-R]
                                    DCDC1_SICB[DC-DC Conv.<br>OUT: 5V 6A]
                                    MC1_SICB[mbed]
                                    DCDC2_SICB[DC-DC Conv.<br>OUT:5V 18A]
                                    DCDC3_SICB[DC-DC Conv.<br>OUT:5V 18A]
                                    DCDC4_SICB[DC-DC Conv.<br>OUT:5V 18A]
                                    DCDC5_SICB[DC-DC Conv.<br>OUT:5V 18A]
                                    DCDC6_SICB[DC-DC Conv.<br>OUT:5V 18A]
                                    
                                    CON1_SICB ==> DCDC1_SICB ==> MC1_SICB
                                    CON1_SICB ==> DCDC2_SICB
                                    CON1_SICB ==> DCDC3_SICB
                                    CON1_SICB ==> DCDC4_SICB
                                    CON1_SICB ==> DCDC5_SICB
                                    CON1_SICB ==> DCDC6_SICB
                                    CON2_SICB -..- MC1_SICB
                                end
                                WH1_SIDC{{Indicator Wire Harness}}
                                WH2_SIDC{{Indicator Wire Harness}}
                                WH3_SIDC{{Indicator Wire Harness}}
                                WH4_SIDC{{Indicator Wire Harness}}
                                WH5_SIDC{{Indicator Wire Harness}}
                                subgraph LLP1["FrontRight LED Graphics Panel (Waterproof Enclosure)"]
                                    LMS1[LED Full Color Matrix<br>NeoPixel RGB Matrix Sheet<br>IN: 5Vdc]
                                end
                                subgraph LLP2["FrontLeft LED Graphics Panel (Waterproof Enclosure)"]
                                    LMS2[LED Full Color Matrix<br>NeoPixel RGB Matrix Sheet<br>IN: 5Vdc]
                                end
                                subgraph LLP3["StarboardSide LED Graphics Panel (Waterproof Enclosure)"]
                                    LMS3[LED Full Color Matrix<br>NeoPixel RGB Matrix Sheet<br>IN: 5Vdc]
                                end
                                subgraph LLP4["PortSide LED Graphics Panel (Waterproof Enclosure)"]
                                    LMS4[LED Full Color Matrix<br>NeoPixel RGB Matrix Sheet<br>IN: 5Vdc]
                                end
                                subgraph LLP5["Rear LED Graphics Panel (Waterproof Enclosure)"]
                                    LMS5[LED Full Color Matrix<br>NeoPixel RGB Matrix Sheet<br>IN: 5Vdc]
                                end

                                DCDC2_SICB ==>|5V| WH1_SIDC
                                MC1_SICB -->|??| WH1_SIDC
                                WH1_SIDC ---|Power + ??| LMS1
                                DCDC3_SICB ==>|5V| WH2_SIDC
                                MC1_SICB -->|??| WH2_SIDC
                                WH2_SIDC ---|Power + ??| LMS2
                                DCDC4_SICB ==>|5V| WH3_SIDC
                                MC1_SICB -->|??| WH3_SIDC
                                WH3_SIDC ---|Power + ??| LMS3
                                DCDC5_SICB ==>|5V| WH4_SIDC
                                MC1_SICB -->|??| WH4_SIDC
                                WH4_SIDC ---|Power + ??| LMS4
                                DCDC6_SICB ==>|5V| WH5_SIDC
                                MC1_SICB -->|??| WH5_SIDC
                                WH5_SIDC ---|Power + ??| LMS5
                            end
```
