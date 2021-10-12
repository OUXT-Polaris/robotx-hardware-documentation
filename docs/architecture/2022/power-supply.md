


## Battery Cluster for Controller

``` mermaid
flowchart TB
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:5px;
    classDef lowPowerSupply stroke-width:3px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==================
    style BA1 fill:#808080,stroke:#808080,color:#fff
    style BA2 fill:#808080,stroke:#808080,color:#fff
    style BA3 fill:#808080,stroke:#808080,color:#fff
    style IDM1 fill:#808080,stroke:#808080,color:#fff
    style IDM2 fill:#808080,stroke:#808080,color:#fff
    style IDM3 fill:#808080,stroke:#808080,color:#fff
    style IDM4 fill:#808080,stroke:#808080,color:#fff
    %% ==================

    subgraph BA1[Battery Assy]
        CON5_BWH_BA1([Socket/Plug]):::highPowerSupply
    end
    subgraph BA2[Battery Assy]
        CON5_BWH_BA2([Socket/Plug]):::highPowerSupply
    end
    subgraph BA3[Battery Assy]
        CON5_BWH_BA3([Socket/Plug]):::highPowerSupply
    end                            
    subgraph PSB1["Power Supply Box for Controller (Waterproof Box)"]
        CON1_PSB1([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        CON2_PSB1([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        CON3_PSB1([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        CON4_PSB1([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        CON6_PSB1([RJ-45 Connector<br>ENRW-28SC5E-R])
        subgraph IDM1[Ideal Diode Module]
            CON1_IDM1(["Pinheader"])
        end
        subgraph IDM2[IDM]
            CON1_IDM2(["Pinheader"])
        end
        subgraph IDM3[IDM]
            CON1_IDM3(["Pinheader"])
        end
        subgraph IDM4[IDM]
            CON1_IDM4(["Pinheader"])
        end
        TB[Terminal]:::highPowerSupply
        KS[Kill Switch Power Relay<br>G9EC-1-B<br>Normally Open Contact 200A]:::highPowerSupply
        MC1[Mbed Extended Board<br>IN: 5V]
        PD1_PSB1[Power Distributor ch1<br>FUSE: ??A]:::lowPowerSupply
        PD2_PSB1[Power Distributor ch2<br>FUSE: ??A]:::lowPowerSupply
        PD3_PSB1[Power Distributor ch3<br>FUSE: ??A]:::lowPowerSupply
        PD4_PSB1[Power Distributor ch4<br>FUSE: ??A]:::lowPowerSupply
        PD5_PSB1[Power Distributor ch5<br>FUSE: ??A]:::lowPowerSupply
        PD6_PSB1[Power Distributor ch6<br>FUSE: ??A]:::lowPowerSupply

        CON1_PSB1 ==>|/2 24Vdc| IDM1
        CON2_PSB1 ==>|/2 24Vdc| IDM2
        CON3_PSB1 ==>|/2 24Vdc| IDM3
        CON4_PSB1 ==>|/2 24Vdc| IDM4
        
        IDM1 & IDM2 & IDM3 & IDM4 ===> TB
        TB ==>|24Vdc| KS
        KS ==>|24Vdc| PD1_PSB1 & PD2_PSB1 & PD3_PSB1 & PD4_PSB1 & PD5_PSB1 & PD6_PSB1
        CON1_IDM1 & CON1_IDM2 & CON1_IDM3 & CON1_IDM4 <--> MC1
    end
    
    CON5_BWH_BA1 ==>|/2  24Vdc| CON1_PSB1
    CON5_BWH_BA2 ==>|/2  24Vdc| CON2_PSB1
    CON5_BWH_BA3 ==>|/2  24Vdc| CON3_PSB1
    DUM1[" "]:::dummy ------- KS
    DUM2[" "]:::dummy -.- CON6_PSB1 -..- MC1
```


## Ideal Diode Module

``` mermaid
flowchart LR
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:5px;
    classDef lowPowerSupply stroke-width:3px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==================
    style TB1 stroke-dasharray:12 3
    style TB2 stroke-dasharray:12 3
    %% ==================

    subgraph PCB[PCB]
        subgraph TB1[IN]
            SM1(("Screw<br>(A)")):::highPowerSupply
            SM3(("Screw<br>(GND)")):::highPowerSupply
        end
        subgraph TB2[OUT]
            SM2(("Screw<br>(K)")):::highPowerSupply
            SM4(("Screw<br>(GND)")):::highPowerSupply
        end
        HSS[High Side Switch<br>MOSFET]:::highPowerSupply
        ICS[Current Sensor]:::highPowerSupply
        IDC[Ideal Diode Controller]
        BUZ[Reverse Notification Buzzer]
        UVD[Under Voltage Detector]
        CON1(["Pinheader"])
        
        SM1 ==> HSS ==> ICS ==> SM2
        SM3 ====> SM4
        SM1 --- BUZ & UVD
        HSS --- IDC ---|isolated| CON1
        UVD ---|isolated| CON1
        ICS ---|isolated| CON1
    end
    
    DUM1[" "]:::dummy ===|/1| SM1
    SM2 ===|/1| DUM2[" "]:::dummy
    DUM3[" "]:::dummy ===|/1| SM3
    SM4 ===|/1| DUM4[" "]:::dummy
    CON1 --- DUM5[" "]:::dummy
```



## Battery Assy


``` mermaid
flowchart LR
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:5px;
    classDef lowPowerSupply stroke-width:3px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==================
    style BU1 fill:#808080,stroke:#808080,color:#fff
    style BU2 fill:#808080,stroke:#808080,color:#fff
    %% ==================

    subgraph BU1[Battery Unit]
        CON1_BU1(["Pin/Recept (+)"]):::highPowerSupply
        CON2_BU1(["Pin/Recept (-)"]):::highPowerSupply
    end
    subgraph BU2[Battery Unit]
        CON1_BU2(["Pin/Recept (+)"]):::highPowerSupply
        CON2_BU2(["Pin/Recept (-)"]):::highPowerSupply
    end
    subgraph BWH["Battery Wire Harness"]
        CON1_BWH([Socket/Plug<br>SurLok Plus]):::highPowerSupply
        CON2_BWH([Socket/Plug<br>SurLok Plus]):::highPowerSupply
        CON3_BWH([Socket/Plug<br>SurLok Plus]):::highPowerSupply
        CON4_BWH([Socket/Plug<br>SurLok Plus]):::highPowerSupply
        WH1{{LKGB 22sq 白}}:::highPowerSupply
        WH2{{LKGB 22sq 白}}:::highPowerSupply
        WH3{{LKGB 22sq 白}}:::highPowerSupply
        CON5_BWH([Socket/Plug<br>HVSLS600062A125]):::highPowerSupply

        CON1_BWH ==> WH1
        CON2_BWH & CON3_BWH ==> WH2
        CON4_BWH ==> WH3
        WH1 & WH3 ==> CON5_BWH
    end
    
    CON1_BU1 ==> CON1_BWH
    CON2_BU1 ==> CON2_BWH
    CON1_BU2 ==> CON3_BWH
    CON2_BU2 ==> CON4_BWH

    CON5_BWH ===|/2| DUM1[" "]:::dummy
```

## Battery Unit

``` mermaid
flowchart LR
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:5px;
    classDef lowPowerSupply stroke-width:3px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==================
                            
    LAB1[[Lead Acid Battery<br>U1-36NE<br>OUT: 12V 36Ah]]:::highPowerSupply
    subgraph BTB["Battery Terminal Box"]
        CBG1([Cable Ground<br>RM20S-12S])
        CBG2([Cable Ground<br>RM20S-12S])
        FS[FUSE: 200A]:::highPowerSupply
        CON1(["Pin/Recept (+)<br>SurLok Plus"]):::highPowerSupply
        CON2(["Pin/Recept (-)<br>SurLok Plus"]):::highPowerSupply
        
        CBG1 ==> FS ==> CON1
        CBG2 ===> CON2
    end

    LAB1 === CBG1
    LAB1 === CBG2

    CON1 ===|/1| DUM1[" "]:::dummy
    CON2 ===|/1| DUM2[" "]:::dummy
```
