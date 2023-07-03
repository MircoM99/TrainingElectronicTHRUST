# Training for the new member of the electronic team

In this repository there are all the material for the trainging of the new member of the electronic team of THRUST.

## First part
In the firts part we will talk about analog eletronic and how we use it. So we will talk about OpAmp, INA and conditioning circuits. We will see how to use temperature sensors, pressure sensors and load cell.
After that we will see a brief overview on the power electronic part inside our electronic, so we will talk about MOSFET and Boost Converter.

You can find some useful references inside the AnalogElectronic directory.

Useful links:
- https://www.analog.com/en/education/education-library/op-amp-applications-handbook.html
- https://www.analog.com/en/education/education-library/data-conversion-handbook.html
- https://www.analog.com/en/education/education-library/linear-circuit-design-handbook.html
- https://www.analog.com/en/education/education-library/high-speed-design-techniques.html

## Second part
In the second part of the training we will see the microcontroller STM32 and how to use it.
First of all you need to dowloand and install it the IDE from ST:
 - https://www.st.com/en/development-tools/stm32cubeide.html
 
After that we will see how to use: GPIO, Interrupt, Timers, DMA, ADC and USART.

You can find some useful references inside the uC directory.

### Exercise 1
Write a software wich convert 5 ADC channels (using DMA) and send the data to the PC through the UART. The data conversion must be triggered by the external
blue button and must continue until it is pressed again. The conversion must be done every 500ms. One the ADC is converting the external green LED must be turned ON.

So: 1 click-> ADC starts to convert every 500ms, 1 click-> ADC stops, 1 click-> ADC start to convert ...

HINT:

1.	To wait use: HAL_Delay(Delay), where Delay is expressed in [ms]
2.	Use a "Flag" to check if the blue button has been pressed

### Exercise 2
Let's consider to have a potentiometer connected on the channel 0 of the ADC, so you can change the voltage on the 
pin rotating the potentiometer, and 6 LED from pin D13-D8. Implement a software which read the ADC channel every 2ms 
using TIM3 and turn on a number of LED proportional to the voltage read on the channel. 
For example if the ADC read a voltage of 3.3/2V the sofware turns on 3 LED and so on...
Implement the software with a function which has as input the value converted by the ADC and the function perform the LED control.
The function should have this name:

```c
	LED_Driver(uint16_t valADC){
	...
	}
```



At the end of the course there will be a small exam.

## Safety courses
In order to garantee the acess of the THRUST Laboratory for the next future you should attend some Safety courses mandatory for the 
university of Padova.

You should do the general training 4h (italian or english language as you prefer):

	- https://elearning.unipd.it/formazione/course/index.php?categoryid=39

and then the high risk course 12h (italian or english language as you prefer):

	- https://elearning.unipd.it/formazione/course/index.php?categoryid=40
	
	


