# Overview      
The device receives an audio signal from a 3.5mm jack (i.e. a headphone jack) that is connected to any analog sound source. The audio signal is then separated into the **7 music frequency ranges** and their respective volumes' are then **displayed on 10 LED's using a decibel scale.**
The brightness of the LEDs and the maximum value of the decibal scale can be adjusted by the user by turning the potentiometers located at the bottom of the PCB shown in *Figure 1*!

![Full_3D_View](https://github.com/GhanGhan/Music_Visualizer/assets/17633599/c1a8e4e7-99a0-4a1e-9c01-7bc1968a0fe4)
***Figure 1: 3D View***
<!---
Hello world

<figure>
   <img src="https://github.com/GhanGhan/Music_Visualizer/assets/17633599/c1a8e4e7-99a0-4a1e-9c01-7bc1968a0fe4">
   <figcaption>**Figure 1: 3D View of Music Visualizer**</figcaption>
</figure>
--->

# Table of Contents
1. Summary of Functionaity
2. Operation Videos
3. Contained in Respository
4. Repository Structure
5. Folder & Design File Explanation
6. Generate Files for Fabrication
7. Current Issues
8. License
9. Acknowledgements

# Summary of Functionality
- Can change input source to a male or female jack using a slide switch as shown in *Figure 2*
- Can safely handle a differential input voltage signal of up to 32V
- Uses 6th order 60dB/decade active Butterworth filters to segment the signal into 7 spectrums
- Both the brightness of the LEDs and maximum scale voltage can be changed using logarithmic potentiometers
   - ** Due to how signal is processed by the filters, the maximum value of the volume scale is 3.5V
- 10 LEDS are used to display the volume of each spectrum as a percentage of the max value of the volume scale
   - 4 Blue LEDs     [4% : 12%]
   - 3 Yellow LEDS   [12% : 35%]
   - 3 Red LEDS      [35% : 100%]
![Block Diagaram](https://github.com/GhanGhan/Music_Visualizer/assets/17633599/5a0be6d4-ff8d-4974-a6ca-7c313b8ab329)
***Figure 2: Block Diagaram of Signal, Power and Control Flow***

# Contained in Repository
- Spice design files (made using LTSpice)
- Schematic Capture and PCB layout (designed in KiCAD)
- Bill-of-Materials BOM
- Other important documents:
   - Sound characterization
   - Measured Frequency response
   - Docs related to properties of critical electrical components

# Operation Videos
[![Frequency_Sweep_Thumb25](https://github.com/GhanGhan/Music_Visualizer/assets/17633599/8c1dfab0-af1a-4b25-96a9-9ba85844304b)](https://www.youtube.com/watch?v=qO5JhvR4XTk)
[![Visualization_Thumb25](https://github.com/GhanGhan/Music_Visualizer/assets/17633599/ac29a39c-50f7-4dd3-bab8-604cce5e9d9b)](https://www.youtube.com/watch?v=t0gG-SFj2FQ)
[![Capabilities_Thumb25](https://github.com/GhanGhan/Music_Visualizer/assets/17633599/a560ecb0-c9c4-47fc-94c8-9cfc0b1c2e9e)](https://www.youtube.com/watch?v=kU3bXjiCjgI)




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
│   │   ├── Coloured_LEDs
│   │   │   ├── LED D5 - Blue_cutted.step
│   │   │   ├── LED D5 - Red_cutted.step
│   │   │   └── LED D5 - Yellow_cutted.step
│   │   ├── DC_Power_Jack
│   │   │   ├── CUI_DEVICES_PJ-079BH.step
│   │   │   ├── CUI_DEVICES.kicad_mod
│   │   │   └── PJ-079BH.lib
│   │   ├── Female_Audio_Jack
│   │   │   └── SJ-3523-SMT-TR--3DModel-STEP-56544.step
│   │   ├── LM3915_LED_Driver
│   │   │   └── LM3915N-1.lib
│   │   ├── Linear_Voltage_Regulator
│   │   │   ├── DIP794W45P254L959H508Q8.kicad_mod
│   │   │   └── LT1054IPE4.step
│   │   ├── PTV09A_Pot_Vertical
│   │   │   ├── PTV09.kicad_mod
│   │   │   └── PTV09A-4225F-B104.step
│   │   ├── PW_On_Off_Switch
│   │   │   ├── E-SWITCH_RR511D1121.kicad_mod
│   │   │   └── RR511D1121.step
│   │   ├── Slide_Switch
│   │   │   ├── OS102011MS2QN1.step
│   │   │   └── SW_OS102011MS2QN1.kicad_mod
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
        │   ├── FinalBassFilterBuf.asc
        │   ├── FinalBrillianceFilterBuf.asc
        │   ├── FinalLowMidrangeBuf.asc
        │   ├── FinalMidrangeFilterBuf.asc
        │   ├── FinalPresenceFilterBuf.asc
        │   ├── FinalSubBassFilterBuf.asc
        │   ├── FinalUpperMidrangeFilterBuf.asc
        │   └── LM324.txt
        ├── Ideal_Filters
        │   ├── BassFilterSK.asc
        │   ├── BrillianceFilterSK.asc
        │   ├── LowMidrangeSK.asc
        │   ├── MidrangeFilterSK.asc
        │   ├── PresenceFilterSK.asc
        │   ├── SubBassFilterSK.asc
        │   └── UpperMidrangeFilterSK.asc
        └── JsonFiles
            ├── Bass Filter.asc
            ├── Brilliance Filter.asc
            ├── Low-Midrange.asc
            ├── Midrange Filter.asc
            ├── Presence Filter.asc
            ├── Sub-Bass Filter.asc
            └── Upper-MidrangeFilter.asc
  ```
# Folder & Design File Explanation
## Documents
- **BOM_Final:** The project Bill-Of-Materials (BOM)
   - Shows all the components that were used, the quantity of each, the prices, model number and where they were sourced from
- **LED Driver IC:** Comparison of the simulated characteristics and values found from breadboarding
- **MaxIoOfEachFilterStage:** Maximum possible current being output by each op-amp of each stage of every filter
- **Sound Characterization:** Shows voltages that were outputted from the audio jack the device was tested on, bandwidth and corner frequency of each spectrum, and steps of the volume-meter
## Schematic_PCB\Music Visualizer (KiCad Folder)
- **Project_Library:** Contains nesseccary .step files (3D models), .lib files (schematic symbols) and/or .kicad_mod files (PCB footprint)  of the DC power jack, female audio jack, LED driver, -5V Inverter & Regulator, potentiometer, On/Off rocker switch switch and slide switch.
    - If any of the file types for any of the circuit elements is not included in the associated sub-folder of the 'Project Library then it is provided by the programs 'Global Library'.
- **Music_Visualizer.kicad_pcb:** PCB layout file for the entire project.
- **Music_Visualizer.kicad_sch:** Main schematic layout file.
    - Contains all 7 frequency spectrums based on the spice files in Simulated_Circuits\Spectrum_Filter\Final_Filter folder.
    - Contains the Audio input circuit (male and female connections where a slide switch is used to choose one or the other), the mounting holes, and op amp bypass capacitors.
    - Contains the Power.kicad_sch and LED_driver.kicad_sch schematics as well
    - **Power.kicad_sch:** Contians circuit for the the +5V regulator, circuit to connect to external power supply with with reverse voltage protection  and -5V Inverter/Regulator as shown in *Figure 3*, the latter 2 are based on the spice files in Simulatd_Circuits\Power.
![Power_Circuitry](https://github.com/GhanGhan/Music_Visualizer/assets/17633599/6fd94c75-fecc-4399-8b48-76c08bde1816)
***Figure 3: 9V & +/-5V Power Circuitry***

    - **Led_Driver.kicad_sch:** Contains the 7 LED drivers, LED brightness control and Rhi-Value Control Circuit based on the spice files in LED_Driving folder.
- **Music_Visualizer.kicad_pro:** Music Visualizer KiCad File.  When clicked it opens up a directory that allows you to access the PCB layout file and schematic layout file.
- Rest of the files are either self explanatory of support files for the KiCad program
## Simulated_Circuits
- **Entire Circuit\Full_Visualizer.asc:** A spice file that contains the 7 spectrum filters being driven by the input signal that contains a frequency from each of the spectrums.  Each of the filters is driving one of the ICs in the LM3915_Chain circuit.  Voltage dividers are used in place of potentiometers to model how turning their knobs allows for control of the LED brightness and scale of the volumeter.
    - **LM324.txt:** A text file that contains the 'macromodel' of the LM324 operational amplifier, allowing it to be used in spice files
- **Filters_With_LED_Drivers:** Contains a spice file for every spectrum filter that driving an LM3915_Base_Circuit.  Also contains an LM324.txt file.
- **LED_Driving:**
    - **LM3915_Base_Circuit.asc:** Contains an LM3915 (the led driver) IC connected to 10 LEDs as shown in *Figure 4*.  The IC is driven by a sinusoidal voltage source.  **Vref (Current reference pin)** is used to set the diode current to about 18mA using a grounded 674 ohm resistor.  It is powered by 9V, and **Vrhi (high-input reference-voltage)** is set to 3.5V.
![Base_DriverV2](https://github.com/GhanGhan/Music_Visualizer/assets/17633599/26bce2fd-7e98-4d7b-9c52-f342392a84c2)
***Figure 4: LED Driving Circuit Prototype***

    - **LM3915_Chain.asc:** Contains 7 LM3915_Base circuits all driven by the same input AC voltage and high-input reference voltage.  Instead of ground, the 674 ohm resistor of each LM3915_Base circuit is connected to a grounded 10kohm potentiometer.  Changing the resistance of the potentiometer allows one to adjust the current going through the LEDs of all of the LED drivers.
    - **RhiControl_LTC1250.asc:** Connects to the high-input reference voltage pin (*Rhi in Figure 4*) of the LED driver IC as shown in *Figure 5*.  R1 and R2 act as a potentiometer. A voltage follower is appended to the ouput of the 'potentiometer' because the average load voltage of the Vrhi pin is about 17.5kohm, when there are in parallel the equivalent reisistance is about 2.5kohm.  The voltage follower ensures that the voltage at the pins is is the same value as the output of the potentiometer.  This particular op-amp was chosen because it has a max input offset voltage of < |10uV|, this means that the voltage at the pin will always be within 10uV of the desired voltage.
![RhiControl_LTC1250_Enlarged](https://github.com/GhanGhan/Music_Visualizer/assets/17633599/f9c4c75c-1733-49de-9c02-a8194e059f68)
***Figure 5: Volume Scale Range Control Circuit***
  
    - **Voltage_Follower_Replacement.asc:**  This is a common-collector circuit, a single transistor implementation of a current follower.  The 2N2222 transistor is used to replace the LTC1250 op-amp because it shorted the -5 and +5 terminals that it was being powered from.
- **Spectrum_Filters:**
    - **Final_Filters:** Folder contains the final filter design for the 7 spectrum filters; Sub-Bass, Bass, Low-Midrange, Midrange, Upper-Midrange, Presence and Brilliance.  Each filter is prepended with a voltage buffer to isolate themselves from the signal source.  This way the impedances of the filters do not affect each other.  Each filter also has a high-pass filter appended to it to prevent unintented activation of the LED driver due to the input-offset voltage of the LM324 op amps which can be as high as 7mV.  *Figure 6* displays the Sub-Bass filters, all of the spectrum filters have the same topology.
  ![SubBaseFinalFilter](https://github.com/GhanGhan/Music_Visualizer/assets/17633599/730bfdd8-ce0e-4ce2-9230-ffa1209b6b4e)
***Figure 6: Complete Sub-Base Filter**

         - Also the resistor values in the final design are slightly different from the "ideal version".  This is because those resistances need at least two resistors in series or parallel to be realized.  The nominal resistor values choses for the final design are within 1.5% of the ideal value.  It was determined that this did not have a significant effect on the frequency response. 
    - **Ideal_Filters:** Folder contains design for idealized implementation of the 7 spectrum filters.  In these LTSpice files ideal op-amps are being used and all of the resistor values match the values provided from the Analog Filter Wizard.
    - **JsonFiles:** The spectrum filters were designed using Analog Devices 'Analog Filter Wizard'.  Once you've inputted the specifications "Passband gain, corner frequency, bandwidth, stopband, center frequency, stages etc."  These are the saved specification files of the Analog filter Wizard for each filter.
         - The center frequency saved in these files are different from the actual center frequency of the filters because (for unidentified reasons) when the correct center frequency was inputted to wrong corner frequencies were outputed.  The center frequency contained in these files gives filters with the correct corner frequencies.

# Generate Files for Fabrication
- If you want to generate the Gerber and Drill files so that the project can be fabricated by a JLCPCB, follow the steps of this website: https://jlcpcb.com/help/article/16-How-to-generate-Gerber-and-Drill-files-in-KiCad-6

# Current Issues
- The last stage of the sub-bass filter generates a power 343Hz wave on its own that is so powerful it activates all of the associated LEDS.  
- The LT1054 op amp shorts the +5 and -5 power rails together and destroys itself in the process.  The is why it was replaced with a Common Collector circuit.

# License
- [![License: CC BY 3.0](https://img.shields.io/badge/License-CC%20BY%203.0-lightgrey.svg)](https://creativecommons.org/licenses/by/3.0/)
- This project is licensed under the [Creative Commons Attribution 3.0 Unported License](https://creativecommons.org/licenses/by/3.0/).
  
# Acknoledgments
- I would like to thank Snap EDA for providing me with the necessary step, kicad_mod and lib files.
- I would like to thank the YouTube Channel "Phil's Lab" for making videos that allowed me to easily learn to use KiCad 6.
  

