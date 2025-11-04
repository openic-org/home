# Controller



The adapter consists of a 36-pin Omnetics connector, a 12-pin Omnetics connecotr, a 16-pin Omnetics connector, a power management unit (PMU) block, a microcontroller unit (MCU), and a programmer connector. This system is shown in the figure below.


``` mermaid
graph LR
    %% PCB Definition
    PCB1[Headstage]

    subgraph PCB2[Controller]
        direction LR

        subgraph b5["PMU-MCU"]
            direction TB
            c1[PMU]
            c2[MCU]
            c1 --> c2
        end

        conn1["Omnetics-16
               Conn"]
        conn0["Omnetics-12
               Conn"]
        subgraph b4["36-Pin Conn"]
            e6[12]
            e7[14]
            e8[10]
        end

        e6 <--> conn0
        e6 <--> b5    
        e7 <--> conn1
        e8 <--> b5
    
    end
    
    b0["128
        Electrode
        Array"]
    b1[Conn]

    %% Top-level connections
    b0 <--> b1 <--> PCB1
    PCB1 <----> b4
    conn1 <--> i1["Intan Rec/Stim
                 Controller"]
    conn0 <--> i0["Intan Rec
                 Controller"]
    b5 <--> Programmer
    
```

<p style="text-align:center"><i><b>Figure 1.</b> System architecutre of the Adapter.</i></p>

We describe each block/component below:

<p style="text-align:center"><i><b>Table 1.</b> Headstage components.</i></p>

| Block/Component  |   Part/Page   | Manufacturer | Description                                                  |
| :--------------: | :-----------: | :----------: | :----------------------------------------------------------- |
|   36-Pin Conn    |       X       |   Omnetics   | 36-pin connector.                                            |
| Omnetics-12 Conn |       X       |   Omnetics   | 12-pin connector compatible with Intan Recording Controller. |
| Omnetics-16 Conn |       X       |   Omnetics   | 16-pin connector compatible with Intan Rec/Stim Controller.  |
|    PMU Block     |      PMU      |     N/A      | Power management unit receiving +3.3V and generating +/-9V and +3V for the analog muxes and MCU. |
|    MCU Block     |      MCU      | ST Microelectronics | STM32U083RC microcontroller unit which programs the analog muxes. |

<br>

