# Single-switch-capacitor-battery-balance
Active balancing system simulink and PCB designer with Altium designer.

It uses (n + 5) keys and only 1 capacitor to balancen cells. It is one of the most common charge-shuttling techniques and is also called fly
capacitor. In this method, the capacitor charges from the cell with the highest voltage and discharges in the cell with the lowest voltage according to the selection. 
Although this method provides balancing in a short time, it requires many keys. Uses a simple
control strategy. 

![image](https://user-images.githubusercontent.com/62069736/88974211-f25daa80-d2c0-11ea-9ee2-bfc737a323bf.png)

With the help of a bi direction converter connected to the SSC system, the batteries are charged and discharged through the capacitor.

![image](https://user-images.githubusercontent.com/62069736/88974578-862f7680-d2c1-11ea-8210-d508d9884770.png)

## General topology explanations
- There are 9 batteries inside each module (n + 5).
- These switches are a structure consisting of 2 N-channel mosfet’s called bi-directional
structures. This structure is briefly made in a controlled way of current flow in
both streams.
- Parallel single capacitor to ensure the need for balancing and smoothness.
- All the switches in the circuit are driven by the PWM signal.
- Selection of high and low energy batteries after determining the Pwm signal.
- For the low energy charge charge, 90% is selected as shown.

![image](https://user-images.githubusercontent.com/62069736/88974835-ea523a80-d2c1-11ea-9774-0499aaf86a1f.png)

- For the discharge of the high energy battery, 10% is selected as shown.

![image](https://user-images.githubusercontent.com/62069736/88974947-12da3480-d2c2-11ea-868b-a4c636d1e6d2.png)

### Bidirectional switch structure 
The structure allows current to flow in both directions. The direction of the
current is determined according to the voltage differences at the two ends. N-channel
is a combination of two mosfets. "IRFB3806PBF" can be used as Mosfet. All switches,
except the converter key in the topology, are bi-directional.

![image](https://user-images.githubusercontent.com/62069736/88975055-41f0a600-d2c2-11ea-8306-8603dd013a53.png)

###  Bidirectional converter
It has been used to support and isolate batteries’ charge and discharge. In line
with the information received from the microcontrollers, the switches of the low voltage
battery are activated and brought to the converter boost position. The opposite of the
same process, with the activation of the high voltage battery, the converter is placed
in the buck position and the battery is charged. 

![image](https://user-images.githubusercontent.com/62069736/88975309-a27fe300-d2c2-11ea-8e7c-bafe34f6f76c.png)

## MATLAB / simulink design of general system topology

![image](https://user-images.githubusercontent.com/62069736/88975403-c9d6b000-d2c2-11ea-8d90-8fed6c763db0.png)

### Simulation Results
- Module 1 values:%20, %40, %80, %20 SOC for cell 1, 2, 3 and 4 respectively.

There are a total of 4 batteries in 1 module. The simulation time of each battery had
to be limited to 30 minutes. The total simulation time for 1 Module took 2 hours. This
is because the batteries need to be balanced individually.

Let’s first look at the SOC comparisons.

![image](https://user-images.githubusercontent.com/62069736/88975836-a2341780-d2c3-11ea-9b31-87b753ffd46c.png)

Comparison of volt values.

![image](https://user-images.githubusercontent.com/62069736/88975883-bb3cc880-d2c3-11ea-9a68-f7a61ae919a0.png)

## Altium designer circuit design

![image](https://user-images.githubusercontent.com/62069736/88977675-05737900-d2c7-11ea-8a57-56601f5e194b.png)

![image](https://user-images.githubusercontent.com/62069736/88977956-7c107680-d2c7-11ea-9da3-a275ee716eb7.png)
