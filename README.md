# Powering-Up-an-Arm-Robot


![Arm Robot](https://github.com/AbdullahAlshambri/Powering-Up-an-Arm-Robot-/blob/main/ArmRobot.jpeg?raw=true)

this is a purposed plan to power up an arm robot made by **Smart Methods Est ©**. First a battery will be chosen based on the components ratings and robot's application, then a charging circuit will be provided to charge the battery, finally the battery will be integrated to the robot's electrical circuit.

## This repository includes 
1- Data sheets of the electrical components of the robot.
 
2- Data sheet of the chosen battery.

3- Circuit Diagram of the charging circuit.

4- Circuit diagram of the operating circuit.

5- Circuit Diagram to adjust the voltage regulator (LM317H).


## I - choosing a battery 
Based on the data sheets of the components, ratings are as follows: 

1- 5 X MG955 servo 

Operating voltage:   4.8-6   /          operating current: 350mA-480mA  
       
2- 4 X 775 Ball bearing DC MOTOR

Operating voltage: 6-20 v   /       operating current: 1.2 A @ 12V
   
3- 2 X L 298N motor drivers
 
Operating voltage: 3.2-40 V   /   operating current: 30mA for internal circuit and up to 2 A per channel max.

4- Arduino uno 

Operating voltage: 5v       /        operating current: 40mA per pin  
        
5- raspberry pi 

Operating voltage:  5.2      /      operating current:400mA – 980mA (depends on model)         

Total Amps drawn considering the application of the robot: 6.58 – 7.23 A (without the Arduino and the raspberry pi because they will not draw significant current in this application).

![Battery Chosen](https://github.com/AbdullahAlshambri/Powering-Up-an-Arm-Robot-/blob/main/Battery%20DataSheet/battery.jpeg?raw=true)

Chosen battery is **WP10-12SE** and it is a 12 volts 10 ah battery. Data sheet of the battery can be found in the repository. This battery was chosen so that it can provide the electric demand of the circuit ideally for an hour, beside that it costs about 23 dollars; ion batteries with similar capacity cost almost 4 times the price of this lead-acid battery. Nevertheless, it is important to install buck converters for the servo motors, Arduino, and raspberry pi. 







## II Charging Circuit 

![Charging Circuit](https://github.com/AbdullahAlshambri/Powering-Up-an-Arm-Robot-/blob/main/Circuit%20Diagrams/Charging%20Circuit.png?raw=true)

To charge the battery it is possible to build up a charging circuit with LM317H as a regulator with a simple filter, full-wave rectifier, and a transformer. According to the data WP10-12SE can be charged with 14.4-15 v. 

Another option to charge the battery is to acquire one of the lead acid battery chargers that are available commercially. Moreover, many charging circuits are available in the market cheaply, one of which is DD30CRTA. DD30CRTA can be bought for less than 4 dollars along with a 15-28 v adapter, the circuit module incldes protection. A similar option would be using UC3906 by Texas Instrument. 




## III Electrical Circuit 
![Approximated Circuit](https://github.com/AbdullahAlshambri/Powering-Up-an-Arm-Robot-/blob/main/Circuit%20Diagrams/operation%20circuit.png?raw=true)

This is an approximation of the robot’s electrical circuit (one Drive(L293D), two DC Motors and 2 Servo Motors), connections of the servo motors must pass via a regulator (I purpose lm317H) to step down the voltage. Arduino and raspberry Pi should also be connected to a linear regulator or a buck converter since they operate on 5-5.2 V. If Arduino UNO is used then a servo shield should be used because the Arduino will not have enough pins. 

#### LM317H Circuit 
Lm317H is a cheap adjustable voltage regulator that outputs 1.2 to 37 V (depending on resistance difference) and a current up to 1.5 A. it is used in this circuit to step down the voltage of the battery from 12v to 5 volts for Arduino and raspberry pi and 6 v for the servos. For the servo motors it is the best to connect each two servo motors with 1 voltage regulator to avoid over demanding. 

![LM317H](https://github.com/AbdullahAlshambri/Powering-Up-an-Arm-Robot-/blob/main/Circuit%20Diagrams/LM713H%20circuit.jpeg?raw=true)

LM317H needs a circuit to adjust the output voltage, the circuit consists of two resistors to adjust the output voltage via the following equation: V=1.25+(1.25*R1/R2) (check datasheet for more info or to add protection to the circuit).
