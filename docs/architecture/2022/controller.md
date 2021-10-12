## Central Compute Unit

``` mermaid
flowchart
                            %% ==== classDef ====
                            classDef highPowerSupply stroke-width:5px;
                            classDef lowPowerSupply stroke-width:3px;
                            classDef commentComponent fill:#0000,stroke:#0000;
                            %% ==================
                            subgraph CB[Compute Box]
                                CON1_CB>NRW-207-RM<br>IN: 24V]
                                DCDC1_CB[DC-DC Conv.<br>OUT:19V 6A]
                                DCDC2_CB[DC-DC Conv.<br>OUT:12V 6A]
                                DCDC3_CB[DC-DC Conv.<br>OUT:5V 6A]
                                NUC1[NUC<br>NUC10i7FNH<br>IN:19V 120W]
                                RT1[router]
                                AP1[access point]
                                L2SW1_CB[16 Port Switching Hub<br>????????<br>IN: ????]
                                L2SW2_CB[5 Port Switching Hub<br>GS105-500JPS<br>IN:12V 0.5A]
                                L2SW3_CB[8 Port Switching Hub<br>GS108-400JPS<br>IN:12V 0.5A]
                                L2SW4_CB[5 Port Switching Hub<br>GS105-500JPS<br>IN:12V 0.5A]
                                L2SW5_CB[5 Port Switching Hub<br>GS105-500JPS<br>IN:12V 0.5A]
                                LC1[Livox Conv. 2.0<br>IN:9 to 30V, 12W]
                                LC2[Livox Conv. 2.0<br>IN:9 to 30V, 12W]
                                MC1_CB[mbed for GNSS]
                                MC2_CB[mbed for IMU]
                                
                                CON1_CB ==>|24Vdc| DCDC1_CB & DCDC2_CB & DCDC3_CB
                                DCDC1_CB ===>|19Vdc| NUC1
                                DCDC2_CB ==>|12Vdc| L2SW1_CB & L2SW2_CB & L2SW3_CB & L2SW4_CB & L2SW5_CB & LC1 & LC2
                                DCDC3_CB ====>|5Vdc| MC1_CB & MC2_CB
                                L2SW1_CB -.- RT1 & AP1 & NUC1 & L2SW2_CB & L2SW3_CB & L2SW4_CB & L2SW5_CB
                                L2SW3_CB -.- LC1 & LC2 & MC1_CB & MC2_CB
                            end
```

## Telecommunication

### Remote control Kit

``` mermaid
flowchart LR
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:5px;
    classDef lowPowerSupply stroke-width:3px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==================

    SPH[Smart Phone<br>iPhone]
```