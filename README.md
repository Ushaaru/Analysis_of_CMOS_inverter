# Analysis_of_CMOS_inverter
This project I started is to analyze the basic characteristics of NMOS, PMOS, and CMOS inverter to practically understand my theoretical knowledge.

# 1. DC analysis of NMOS
"Firstly, I simulated the DC characteristics of NMOS using the following tools:
- Xschem for schematic design
- Ngspice for SPICE netlist simulation
- Skywater-130 nm PDK"
- ![image](https://github.com/user-attachments/assets/abb22461-8014-42d6-b682-b243e8d453b8)
- Fig1: Schematic of NMOS.
  
- The plot below shows the DC sweep of Vgs vs. Id for different values of Vds.
  ![image](https://github.com/user-attachments/assets/864d5374-093a-417a-bbc5-d9f07f891985)
Here from this graph we can see threshold voltage is between 0.6V to 0.7V for different value of Vds.

- The plot below shows the DC sweep of Vds vs. Id for different value of Vgs.
- ![image](https://github.com/user-attachments/assets/bb1c68f2-5144-4131-b5f0-697bc24b4f9c)
Here I changed the Vgs to 2.5V and plotted for different Vgs value with 0.5 increment
![image](https://github.com/user-attachments/assets/8f5e8c61-a161-4fe6-b730-5174b7642b79)

- The below plot shows the gm(dId/dVgs) and Ro inverse of (dId/dVgs).
  ![image](https://github.com/user-attachments/assets/21d383d7-663c-45fc-9f15-00db9f1ec75a)![image](https://github.com/user-attachments/assets/0b4c533a-15b4-4b67-a63a-97d8582840f2)

# 2. DC analysis of PMOS
Similarly, for PMOS, I plotted the same characteristics as for NMOS and found that to achieve the same Ids current, the aspect ratio (W/L) for PMOS needs to be 2.5 times the (W/L) of NMOS. This is an important consideration for further CMOS inverter design.
![image](https://github.com/user-attachments/assets/e8f8765f-c135-4da8-9800-ebf9d7a2c132)
I got 500.9 µA for NMOS with Vgs = 1.8V and Vds = 2.2V.
![image](https://github.com/user-attachments/assets/caed9e1b-0a04-4e73-b9a1-7a2329c2561a)
Similarly for pmos 503.47uA with Vgs=1.8V and Vds=2.2V.

# 3. CMOS Inverter Design and Analysis
- Since we know that neither NMOS nor PMOS can drive both high and low values completely, we use a CMOS combination of PMOS and NMOS because PMOS is strong at driving a '1', and NMOS is strong at driving a '0'.
Let's look into the connection of a CMOS (Complementary Metal-Oxide-Semiconductor) inverter.
- PMOS is connected between VDD and Vo because it is strong at driving a '1'.
- NMOS is connected between Vo and GND because it is strong at driving a '0'.
- From this, we can conclude that PMOS is preferred for the pull-up network (PUN), and NMOS is preferred for the pull-down network (PDN).

- 3.1 CMOS Inverter schematic DC Analysis
![image](https://github.com/user-attachments/assets/2a35092c-504d-4e87-86a1-fcec9323d8c9)
![image](https://github.com/user-attachments/assets/14c871f5-b5ba-46c5-a0aa-afc1e8fb778a)
- Fig: Schmatic design of the CMOS inverter
- Let's plot the voltage transfer characteristics(VTC) of CMOS inverter.
Intially I have taken aspect ratio of both pmos and nmos same we can see the output not having good noise margin.
- What is Noise Margin?
  The amount of noise the CMOS can reject without effecting the output is defined as Noise Margin.
  Some of the terminology related to Noise Margin.
  VOH-Maximum output voltage when (logic='1').
  VOL-Minimum ouput voltage when (logic='0').
  VIL-Minimum input voltage
  VIH-Maximum input voltage
  Vm/Vth-Threshold voltage
  - The noise margin of an inverter is defined by Noise Margin Low(NML) and Noise Margin High(NMH).
  NML=VIL-VOL
  NMH=VOH-VIH
  Ideally Vth/Vm should be VDD/2
  So, VDD=1.8V we should get 0.9V
  ![image](https://github.com/user-attachments/assets/97e69423-f0e7-49e4-8c8e-b57c86c96887)
  - Here we got 0.83V Let's try to improve the NM.
  - From the previous PMOS and NMOS characteristics, I calculated the aspect ratio. I set the PMOS
  aspect ratio to 2.5:1, which resulted in a maximum Vm of 0.88V.
  ![image](https://github.com/user-attachments/assets/33537bc3-7631-4f22-aaaf-fde34b05e6a1)
- Let's plot the gain of the CMOS inverter and analyze the NM parameters.
- We have calculated VIL,VOH,VIH and VOL
- ![image](https://github.com/user-attachments/assets/8ec575c9-0b7c-4228-9f0e-386f56165bfa)
  Using gain plot we found out the parameters of Noise margin NMl=VIL-VOL, NMH=VOH-VIH
  we get NML=0.615 NMH=0.643 they are almost equal because we took almost closest to 0.9.
  ![image](https://github.com/user-attachments/assets/c84f7c74-75e7-40a1-b950-54fbce5334ef)
- 3.2 CMOS Inverter Transient DC Analysis
- Let's see the transient simulation of the schematic to calculate propagation delay(tp) of the inverter.
  Here I calculated High to low propagation delay(tphl) and low to high propogation delay(tplh) to calculate tp which is given by tp=(tphl+tplh)/2.
  I got tpHL=27.57ps, tpLH=31.93ps and tp=29.75ps (Propagation delay depends upon the input)
  ![image](https://github.com/user-attachments/assets/9882090c-3f5b-4051-82d1-11728431957d)
- Let's calculate the rise time. It is given by the equation tr=t90-t10 where t90 is the time taken for the output voltage vout rise to 90% of its final value, and t10 is the time taken for it to rise to 10%.
![image](https://github.com/user-attachments/assets/c84f7c74-75e7-40a1-b950-54fbce5334ef)
- The above calculated values are for unloaded external capacitor. Now let's try to improve the tr by chnanging the aspect ratio of nmos and pmos, when I changed the aspect ratio 4:2(ppmos:nmos) I got a increased rise time of 34.60ps from previous where I had aspect ratio 2.5:1, I got 34.85ps.
- Similarly I calculated fall time I got for 4:2 ratio 30.89ps and for 2:5:1 ratio 31.53ps. I see no much changes lets try another method decreasing the supply power to 1V I got a improved rise time and fall time of 58.00ps and 36.51ps.
![image](https://github.com/user-attachments/assets/59a771c2-0037-4a37-ab58-79f66cfa05f8)
- Now I see a increased rise time and fall time when a connected a 0.01pF external capacitor where I got tr=124.2ps and tf=50.2ps this was calculated for 1:1 aspect ratio let me try decreasing capacitor value and increasing aspect ratio.
- Now I changed the external capcitor value to 10fF and aspect ratio 4:2 I got tr=50.0ps and tf=38.1ps
![image](https://github.com/user-attachments/assets/6c6c5a13-51e9-47a4-8302-9f733afa1dfd)
![image](https://github.com/user-attachments/assets/d6c8d4c5-d4c7-4f99-934f-2111c824cac9)
- Now let's calculate the power dissipation of the inverter
- Power is given by integration of (V*I) upon time period we have got power dissipation=-16.69uW for external cap=100fF
- For cap=10fF we got power dissipation=-2.03uF we can see that as we decrease load capacitance power dissipation decreases.
![image](https://github.com/user-attachments/assets/abd20722-a6e0-4936-9450-9c483170881f)
![image](https://github.com/user-attachments/assets/2b20e5a5-d04f-419c-a38f-07cc676a79ea)
