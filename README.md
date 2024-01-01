# Overview      
The device recieves an audio signal from a 3.5mm jack (i.e. and headphone jack) that is connected to any analog sound source.  The audio signal is then seperated into the **7 music frequency ranges** and their respective volumes' are then **displayed on LED's using a logorithmic scale.**
The brightness of the LEDs and the maximum value of the logorithmic scale can be adjusted by the user!
   
Detailed Summary      
•	Separate’s audio signal into the 7 music frequency bands; Sub-Bass, Bass, Low-Midrange, Midrange, Upper-Midrange, Presence and Brilliance by using 6th order active     Butterworth (i.e. Sallen-Key topology) bandpass filters     
•	Volume for each frequency band will be represented using 10 LED’s on a logarithmic scale      
•	LED’s will be driven with the LM3915 IC which will allow for the LED brightness and volume level comparison to be tunable     
•	All sub-circuits are built and tested in LTspice      
•	The PCB for the circuit will be designed using KiCad      
