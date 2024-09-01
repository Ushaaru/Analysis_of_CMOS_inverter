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
