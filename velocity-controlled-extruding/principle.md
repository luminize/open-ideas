# How does it work?

- Before extruding the first line, the width **w1** and height **h1** from **SECTION A-A** are set in the program.
- These two will be the inputs of the calculation for the "gear" ratio between the extruder velocity and the combined (x,y,z) velocity. Depending not only on **w1** and **h1** but also on **∅D** and the ratio between extruder motor steps and filament rollers.
- @ **P1** the movements/velocities of extruder motor and nozzle will be locked (coupled).
- moving **line1** from **P1** to **P2**. The extruder speed is dependant (slave) of the actual speed of the nozzle
- @ **P2** the velocities must be de-coupled
- @ **P2** the extruder must retract some distance of the filament to prevent oozing when travelling from **P3** to **P4**.
- @ **P5** the extruder must prime the previously retracted filament, filling the chamber so the start at **line2** does not miss material.
- just before travelling, the new ratio (because the **SECTION B-B** is different) must be set, and the velocities of nozzle and extruder must be coupled.

# Why?

- During the melting of the filament, there is a period when the filament being heated will have a temperature above the glass transition temperature (**Tg**) but below the melting temperature (**Tmelt**). This is the moment the material looses integrity. Applying pressure to the material makes it expand to the wall of the bore.
- Expanding (melting traject between **Tg** and **Tmelt**) will happen over a varying length **w**.
- Depending on speed of extruding, temperature, material it will take a varying force/pressure to extrude the filament.
- The varying pressure on the filament and the speed of the filament results in a varying height **w** and a hysteresis of the discharge of the material.
- I think it's much more easy to control the actual discharge of the material with the speed of extruder, being calculated by nozzle acceleration, actual nozzle speed (discharge of material) and temperature.
- instead of interpolating (X,Y,Z) position of the nozzle with the (A) position of the extruded filament we interpolate the derivative (speed, not position) of nozzle position and extruder.