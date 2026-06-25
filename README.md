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

## Bill of Materials 

|Item	|Description|	Reference	|Qty	|MOQ|	Value|	Unit Price ($)|	Total Price ($)	|Footprint|	MPN	|URL|
|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
|Capacitor	|Output decoupler|	C1|	1|	25	|0.1uF|	0.0061|	0.15|	Capacitor_SMD:C_0805_2012Metric|	C0805B104K500NT	|[Link](https://www.lcsc.com/product-detail/C476766.html?spm=wm.fly.bg.5.xh___wm.fly.tp.3.ml&lcsc_vid=QQVaAVJeTlJdUVBVE1hcBVFWEwcNBVxeQwAPA1YHFQMxVlNeRlhXVlNWQFReUjsOAxUeFF5JWBYZEEoKFBINSQcJGk4NBhADEA4cHktXRlVcSQwSGg0%3D)|
|Capacitor	|Input decoupler|	C2	|1|	10|	2.2uF|	0.024|	0.24|	Capacitor_SMD:C_0805_2012Metric|	CL21B225KAFNNNE|	[Link](https://www.lcsc.com/product-detail/C19110.html?spm=wm.fly.bg.0.xh___wm.fly.tp.3.ml&lcsc_vid=QQVaAVJeTlJdUVBVE1hcBVFWEwcNBVxeQwAPA1YHFQMxVlNeRlhXVlNWQFReUjsOAxUeFF5JWBYZEEoKFBINSQcJGk4NBhADEA4cHktXRlVcSQwSGg0%3D)|
|Capacitor|	Feed-forward capacitor|	C3|	1|	50|	0.01uF|	0.0094|	0.47|	Capacitor_SMD:C_0805_2012Metric|	CL21B103KBANNNC|	[Link](https://www.lcsc.com/product-detail/C1710.html?spm=wm.fly.bg.0.xh___wm.fly.tp.3.ml&lcsc_vid=QQVaAVJeTlJdUVBVE1hcBVFWEwcNBVxeQwAPA1YHFQMxVlNeRlhXVlNWQFReUjsOAxUeFF5JWBYZEEoKFBINSQcJGk4NBhADEA4cHktXRlVcSQwSGg0%3D) |
|Red & green LEDs|	Lights up upon input|	D1,D2|	1|	100|  LED-RED,LED-GREEN|	0.0143|	1.43|	LED_SMD:LED_0805_2012Metric	|	| [Link](https://www.aliexpress.us/item/3256812235321424.html?spm=a2g0o.productlist.main.9.40ff6dfeufImUM&algo_pvid=1b22d9b3-163a-48fe-a597-e316fd92717e&algo_exp_id=1b22d9b3-163a-48fe-a597-e316fd92717e-8&pdp_ext_f=%7B%22order%22%3A%227%22%2C%22eval%22%3A%221%22%2C%22fromPage%22%3A%22search%22%7D&pdp_npi=6%40dis%21USD%214.08%211.43%21%21%2127.52%219.65%21%402101d9ef17819931688657801eb4d5%2112000058343268106%21sea%21US%217756416958%21X%211%210%21n_tag%3A-29911%3Bd%3A882c3b75%3Bm03_new_user%3A-29895%3BpisId%3A5000000208226559&curPageLogUid=dpkon91Z9mo7&utparam-url=scene%3Asearch%7Cquery_from%3A%7Cx_object_id%3A1005012421636176%7C_p_origin_prod%3A)|
| 2-pin connector|	Power input/output	|J1,J2|	2|	10|	Conn_01x02|	0.0191	|1.91|	Connector_PinHeader_2.54mm:PinHeader_1x02_P2.54mm_Vertical|	|	[Link](https://www.aliexpress.us/item/3256807253955994.html?spm=a2g0o.productlist.main.2.2e9b62b2mTT3WZ&algo_pvid=93b7913f-9a4f-483d-99ae-aac3188ba0c6&algo_exp_id=93b7913f-9a4f-483d-99ae-aac3188ba0c6-1&pdp_ext_f=%7B%22order%22%3A%22789%22%2C%22eval%22%3A%221%22%2C%22fromPage%22%3A%22search%22%7D&pdp_npi=6%40dis%21USD%216.83%211.91%21%21%2146.07%2112.86%21%40210328d417819933313278739edf81%2112000040762755700%21sea%21US%217756416958%21X%211%210%21n_tag%3A-29911%3Bd%3A882c3b75%3Bm03_new_user%3A-29895%3BpisId%3A5000000209180939&curPageLogUid=T0dEK33dI0p0&utparam-url=scene%3Asearch%7Cquery_from%3A%7Cx_object_id%3A1005007440270746%7C_p_origin_prod%3A) | 
|Resistor|	649 Ohms|	R1|	1|100|		649|	0.001|	0.1|	Resistor_SMD:R_0805_2012Metric|	HRC0805F6490FNTN|	[Link](https://www.lcsc.com/product-detail/C55098624.html?s_z=n_q_t_resistor&spm=wm.fly.bg.5.xh___wm.ssy.tc.0.tz&lcsc_vid=QQVaAVJeTlJdUVBVE1hcBVFWEwcNBVxeQwAPA1YHFQMxVlNeRlhXVFBXQVJaVTsOAxUeFF5JWBYZEEoKFBINSQcJGk4eAhYVGA8PCycDGRULFUsLDjEcCA4DFBVBAwESFggC) | 
| Resistor|	280 Ohms|	R2|	1|	100|	280|	0.0031|	0.31|	Resistor_SMD:R_0805_2012Metric|	FRC0805F2800TS|	[Link](https://www.lcsc.com/product-detail/C2960739.html?s_z=n_q_t_resistor&spm=wm.fly.bg.0.xh___wm.ssy.tc.0.tz&lcsc_vid=QQVaAVJeTlJdUVBVE1hcBVFWEwcNBVxeQwAPA1YHFQMxVlNeRlhXVFBXQVJaVTsOAxUeFF5JWBYZEEoKFBINSQcJGk4eAhYVGA8PCycDGRULFUsLDjEcCA4DFBVBAwESFggC) |
| TPS79333|	Regulator|	U1|	1|	5|	TPS79333-EP	|0.3|	1.52|	Package_TO_SOT_SMD:SOT-23-5|	TPS79333DBVR|	[Link](https://www.lcsc.com/product-detail/C9840.html?s_z=n_q_TPS79333&spm=wm.fly.bg.1.xh&lcsc_vid=QQVaAVJeTlJdUVBVE1hcBVFWEwcNBVxeQwAPA1YHFQMxVlNeRlhXVFNXRlNYVzsOAxUeFF5JWBYZEEoKFBINSQcJGk4eFQsCAgIaSgADAwAHC0slQlReXlxQRVVADxALGw%3D%3D) | 
| PCB Fabrication | Producing PCB from JLCPCB | |  1 | | | 2.2 | 2.2 | | | |
| PCB Fabrication | Producing PCB from JLCPCB | |  1 | | | 3.12 | 3.12 | | | |
| **Total**|  |  | 			**11**	|  |  |  |			**11.45**  | 

----

<img width="1410" height="2000" alt="TPS79333 Regulator Board" src="https://github.com/user-attachments/assets/0b8f08eb-441b-4d28-9dd6-68daa8b683b5" />
