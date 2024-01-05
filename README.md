# Overview      
The device receives an audio signal from a 3.5mm jack (i.e. a headphone jack) that is connected to any analog sound source. The audio signal is then separated into the **7 music frequency ranges** and their respective volumes' are then **displayed on 10 LED's using a logorithmic scale.**
The brightness of the LEDs and the maximum value of the logorithmic scale can be adjusted by the user!
   
## Summary of Functionality
- Can change input source to a male or female jack using a slide switch, both of which are single channel
- Can safely handle a differential input voltage signal of up to 32V
- Uses 6th order 60dB/decade active Butterworth filters to segment the signal into 7 spectrums
- Both the birghtness of the LEDs and maximum scale voltage can be changed using logorithmic potentiometers
   - ** Due to how signal is processed by the filters, the maximum value of the volume scale is 3.5V
- 10 LEDS are used to display the volume of each spectrum as a percentage of the max value of the volume scale
   - 4 Blue LEDs     [4% : 12%]
   - 3 Yellow LEDS   [12% : 35%]
   - 3 Red LEDS      [35% : 100%]
## Contained in Repository
- Spice design files (made using LTSpice)
- Schematic Capture and PCB layout (designed in KiCAD)
- Bill-of-Materials BOM
- Other important documents:
   - Sound characterization
   - Measured Frequency response
   - Docs related to properites of critical electrical components

# Repository Structure
```
├── Documents
│   ├── BOM_Final.xlsx
│   ├── LED Driver IC.xlsx
│   ├── MaxIoOfEachFilterStage.xlsx
│   ├── Measured_Frequency_Response.xlsx
│   ├── Sound_Characterization.xlsx
│   └── Trace width vs current.xlsx
├── Schematic_PCB/Music_Visualizer
│   ├── Music_Visualizer-backups
│   ├── Project Library
│   │   ├── DC_Power_Jack
│   │   ├── Female_Audio_Jack
│   │   ├── LM3915_LED_Driver
│   │   ├── Linear_Voltage_Regulator
│   │   ├── PTV09A_Pot_Vertical
│   │   ├── PTV09A_Vert
│   │   ├── PW_On_Off_Switch
│   │   ├── Slide_Switch
│   │   ├── License.txt
│   │   └── how-to-import.htm
│   ├── Music_Visualizer.csv
│   ├── Music_Visualizer.kicad_pcb
│   ├── Music_Visualizer.kicad_prl
│   ├── Music_Visualizer.kicad_pro
│   ├── Music_Visualizer.kicad_sch
│   ├── Music_Visualizer.wbk
│   ├── Music_Visualizer.xml
│   ├── Power.kicad_sch
│   ├── fp-info-cache
│   ├── fp-lib-table
│   └── sym-lib-table
└── Simulated Circuits
    ├── Entire_Circuit 
    │   ├── Full_Visualizer.asc
    │   └── LM324.txt
    ├── Filters_With_LED_Drivers
    │   ├── FinalBassFilterWithLEDDriver.asc
    │   ├── FinalBrillianceFilterWithLEDDriver.asc
    │   ├── FinalLowMidrangeWithLEDDriver.asc
    │   ├── FinalMidrangeFilterWithLEDDriver.asc
    │   ├── FinalPresenceFilterWithLEDDriver.asc
    │   ├── FinalSubBassFilterWithLEDDriver.asc
    │   ├── FinalUpperMidrangeFilterWithLEDDriver.asc
    │   └── LM324.txt
    ├── LED_Driving
    │   ├── LM3915_Base_Circuit.asc
    │   ├── LM3915_Chain.asc
    │   ├── RhiControl_LTC1250.asc
    │   └── Voltage_Follower_Replacement.asc
    ├── Power
    │   ├── LT1054_Inverter_and_regulator.asc
    │   └── Reverse_Voltage_Protection.asc
    └── Spectrum_Filters
        ├── Final_Filters
        │   ├── Final_No_Buffer
        │   ├── Final_With_Buffer
        │   ├── AllFiltersBuf_NonBuf.asc
        │   └── LM324.txt
        ├── Ideal_Filters
        │   ├── BassFilterSK.asc
        │   ├── BrillianceFilterSK.asc
        │   ├── LowMidrangeSK.asc
        │   ├── MidrangeFilterSK.asc
        │   ├── PresenceFilterSK.asc
        │   ├── SubBassFilterSK.asc
        │   └── UpperMidrangeFilterSK.asc
        ├── JsonFiles
        │   ├── Bass Filter.asc
        │   ├── Brilliance Filter.asc
        │   ├── Low-Midrange.asc
        │   ├── Midrange Filter.asc
        │   ├── Presence Filter.asc
        │   ├── Sub-Bass Filter.asc
        │   └── Upper-MidrangeFilter.asc
        └── Real_Filters
            ├── RealBassFilter.asc
            ├── RealBrillianceFilter.asc
            ├── RealLowMidrange.asc
            ├── RealMidrangeFilter.asc
            ├── RealPresenceFilter.asc
            ├── RealSubBassFilter.asc
            ├── RealUpperMidrangeFilter.asc
            └── LM324.txt
  ```
# Folder Explanation
## Documents
- BOM_Final: The project Bill-Of-Materials (BOM)
   - Shows all the components that were used, the quantity of each, the prices, model number and where they were sourced from
- LED Driver IC: Comparison of the simulated characteristics and values found from breadboarding
- MaxIoOfEachFilterStage: Maximum possible current being output by each op-amp of each stage of every filter
- Sound Characterization: Shows voltages that were outputed from the audio jack the device was tested on, bandwidth and corner frequency of each spectrum, and steps of the volume-meter

