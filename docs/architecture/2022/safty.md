## Emergency Stop System

``` mermaid
flowchart LR
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:5px;
    classDef lowPowerSupply stroke-width:3px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==================
    style ESB1 fill:#808080,stroke:#808080,color:#fff
    style ESB2 fill:#808080,stroke:#808080,color:#fff
    style ESB3 fill:#808080,stroke:#808080,color:#fff
    style ESB4 fill:#808080,stroke:#808080,color:#fff
    style PCB stroke-dasharray:5 5
    %% ==================

    subgraph ESB1["On-Board E-Stop Button"]
        CBG_ESB1([Cable Ground])
    end
    subgraph ESB2["On-Board E-Stop Button"]
        CBG_ESB2([Cable Ground])
    end
    subgraph ESB3["On-Board E-Stop Button"]
        CBG_ESB3([Cable Ground])
    end
    subgraph ESB4["On-Board E-Stop Button"]
        CBG_ESB4([Cable Ground])
    end

    subgraph SSCB["Safety System Control Box"]
        LAB[(U1-36NE ???<br>OUT:12V<br>36Ah)]
        MSW1("Manual Switch for Control<br>Contact: SPST NC ALT(1b)")
        MSW2("Manual Switch for Thruster<br>Contact: SPST NC ALT(1b)")
        CON1_SSCB([RJ-45 Connector<br>ROP-5SDFFH-TCU7001])
        
        CON2_SSCB(["E-stop Connector"])
        CON3_SSCB(["E-stop Connector"])
        CON4_SSCB(["E-stop Connector"])
        CON5_SSCB(["E-stop Connector"])

        RCR[Radio Control Reciever]                                
        
        subgraph PCB["E-Stop Logic Board"]
            ORC[Signal ORing Circuit]
            MC1_SSCB[mbed]
            KSD1[Kill Switch Driver]
            KSD2[Kill Switch Driver]
        end

        CON2_SSCB & CON3_SSCB & CON4_SSCB & CON5_SSCB & MSW1 & MSW2 & RCR --- ORC
        MC1_SSCB -.- CON1_SSCB
        ORC --> KSD1 & KSD2
        ORC --- MC1_SSCB
    end
    
    PPL1[Pole Patlite]

    CBG_ESB1 --> CON2_SSCB
    CBG_ESB2 --> CON3_SSCB
    CBG_ESB3 --> CON4_SSCB
    CBG_ESB4 --> CON5_SSCB

    MC1_SSCB ---> PPL1
                
```

### On-Board E-Stop Button

``` mermaid
flowchart LR
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:5px;
    classDef lowPowerSupply stroke-width:3px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==================

    subgraph ENC["Waterproof enclosure"]
        ESS("E-Stop Switch<br>Contact: SPST NC ALT (1b)")
        CBG([Cable Ground<br>RM16S-8S])
    end
    CON(["Plug [IP67]<br>"])

    ESS --- CBG --- CON --- DUM[" "]:::dummy
```

### test

``` mermaid
flowchart LR
    %% ==== classDef ====
    classDef highPowerSupply stroke-width:4px;
    classDef lowPowerSupply stroke-width:2px;
    classDef dummy fill:#0000,stroke:#0000;
    %% ==================
    style IDM1 fill:#808080,stroke:#808080,color:#fff
    style IDM2 fill:#808080,stroke:#808080,color:#fff
    style IDM3 fill:#808080,stroke:#808080,color:#fff
    style IDM4 fill:#808080,stroke:#808080,color:#fff
    style IDM5 fill:#808080,stroke:#808080,color:#fff
    style IDM6 fill:#808080,stroke:#808080,color:#fff
    style IDM7 fill:#808080,stroke:#808080,color:#fff
    style IDM8 fill:#808080,stroke:#808080,color:#fff
    %% ==================

    subgraph ENC[aaa]
        direction LR
        CON1_PSI([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        CON2_PSI([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        CON3_PSI([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        CON4_PSI([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        CON5_PSI([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        CON6_PSI([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        CON7_PSI([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        CON8_PSI([Pin/Recept<br>HVSLS600022A1H6<br>IN: 24Vdc]):::highPowerSupply
        subgraph IDM1[<center>Ideal<br>Diode<br>Module</center>]
            DUM1[" "]:::dummy
        end
        subgraph IDM2[<center>Ideal<br>Diode<br>Module</center>]
            DUM2[" "]:::dummy
        end
        subgraph IDM3[<center>Ideal<br>Diode<br>Module</center>]
            DUM3[" "]:::dummy
        end
        subgraph IDM4[<center>Ideal<br>Diode<br>Module</center>]
            DUM4[" "]:::dummy
        end
        subgraph IDM5[<center>Ideal<br>Diode<br>Module</center>]
            DUM5[" "]:::dummy
        end
        subgraph IDM6[<center>Ideal<br>Diode<br>Module</center>]
            DUM6[" "]:::dummy
        end
        subgraph IDM7[<center>Ideal<br>Diode<br>Module</center>]
            DUM7[" "]:::dummy
        end
        subgraph IDM8[<center>Ideal<br>Diode<br>Module</center>]
            DUM8[" "]:::dummy
        end
        TB1[Terminal Block]:::highPowerSupply
        TB2[Terminal Block]:::highPowerSupply
        IVS1[Isolated Voltage Sensor]
        IVS2[Isolated Voltage Sensor]
        KS1[Power Relay<br>G9EC-1-B<br>SPST NO 200A]:::highPowerSupply
        KS2[Power Relay<br>G9EC-1-B<br>SPST NO 200A]:::highPowerSupply
        PD1[Power Distributor]:::lowPowerSupply
        PD2[Power Distributor]:::lowPowerSupply
        PD3[Power Distributor]:::lowPowerSupply
        CB1["Circuit Breaker<br>80A"]:::highPowerSupply
        CB2["Circuit Breaker<br>80A"]:::highPowerSupply
        MCB1[Mbed Expansion Board<br>IN: 5V]
        CON1_PSO([Socket/Recept<br><br>OUT: 24Vdc]):::highPowerSupply
        CON2_PSO([Socket/Recept<br><br>OUT: 24Vdc]):::highPowerSupply

        CON1_PSI === IDM1
        CON2_PSI === IDM2
        CON3_PSI === IDM3
        CON4_PSI === IDM4
        CON5_PSI === IDM5
        CON6_PSI === IDM6
        CON7_PSI === IDM7
        CON8_PSI === IDM8
        IDM1 & IDM2 & IDM3 & IDM4 === TB1 === KS1 === PD1 & PD2 & PD3
        IDM5 & IDM6 & IDM7 & IDM8 === TB2 === KS2 === CB1 & CB2
        CB1 === CON1_PSO
        CB2 === CON2_PSO
        TB1 --- IVS1 --- MCB1
        TB2 --- IVS2 --- MCB1
        IDM1 & IDM2 & IDM3 & IDM4 <--> MCB1
        IDM5 & IDM6 & IDM7 & IDM8 <--> MCB1
    end
```