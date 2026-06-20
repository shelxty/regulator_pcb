# 5V to 3.3V TPS79333 Regulator Board

<img width="738" height="442" alt="image" src="https://github.com/user-attachments/assets/e143d950-6ecc-4db3-9c0f-17f8a3ae5ce4" />

After a lot of struggle with attempting to understand KiCad (thank you Hack Club Fallout mentors!) I made a simple linear voltage regulator to get started with learning, since this was a project simple enough to actually understand completely (schematic, PCB, everything). It's the first PCB I fully finished, designed in KiCad. I guess it can also be counted as my first actual electronics project! 

This is a tiny breakout board that takes unregulated input voltage (anywhere between around 3.4V to 5V) and outputs clean, fixed 3.3V volts. 

## Custom Features
- **Two LEDs:** This board has a red LED that lights up when input power is applied, and a green LED that confirms the output rail is working and regulating the voltage.
- **Feed-forward capacitor (C3):** On the feedback path, a feed-forward capacitor is set to improve noise rejection.
- **Compactness:** Each part has a footprint of 0805 or smaller, meaning this regulator board is extremely tiny and portable.

...and a very bad drawing I impulsively drew.

## How the Circuit Works (w/ Labels)
| Label | Part | What it Does |
|--------|-------|------------|
| U1 | TPS79333 | The actual regulator, which drops the input voltage to a fixed output of 3.3V | 
| J1 | 2-pin connector | The power input (it takes in unregulated voltage), with a ground pin | 
| J2 | 2-pin connector | The power output (outputs a regulated 3.3V), with a ground pin | 
| C2 | 2.2uF capacitor | Input decoupler (it smoothes out incoming supply before it gets to the regulator) | 
| C1 | 0.1uF capacitor | Output decoupler (keeps the 3.3V rail stable should turbulence arise) | 
| C3 | 0.01uF capacitor | Feed-forward capacitor (improves noise rejection, according to the TI reference design) | 
| R2 | 280Ω resistor | Causes a 1.9V drop (3.3V - 1.9V) / 5mA = 280Ω | 
| R1 | 649Ω resistor | Causes a 1.75V drop (5 - 1.75V) / 5mA = 650Ω | 
| D1 | Red LED | Lights up when input voltage is applied | 
| D2 | Green LED | Lights up when 3.3V voltage is successfully outputted | 

## PCB Design 
This small regulator board is a 2 layer PCB with 2 sets of connectors. 

<img width="916" height="377" alt="image" src="https://github.com/user-attachments/assets/bafce506-c3fb-4181-9db8-8358a56cf897" />

_PCB Editor View_



<img width="1480" height="717" alt="image" src="https://github.com/user-attachments/assets/8cc1ae7e-eaee-4fc9-a912-d440769d7dde" />

_Schematic Editor View (w/ comments & text for beginners to understand because I'm a complete beginner)_

