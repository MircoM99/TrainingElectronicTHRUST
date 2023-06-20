# Training STM32
In this directory there are all the materials necessary to learn the STM32 microcontroller.
You can find Reference and Overview documents which explain the structure of the uC and the HAL_Library.pdf which explain the HAL functions
useful to program the uC.


## Source code
In each directory is present the project for the STM32CubeIDE presented during the training lessons:

## Lesson 1
In the first lesson we take a look at the STM32 IDE enviroments and we develop togheter a simple software which convert 4 ADC channels when the external
button is pressed. The conversion data will be sent to the USART and visualized on Putty.

Firt of all configure the peripherals on the graphic perspective: ADC with DMA, USART and External Interrupt on the Blue Push Button.
After this find the Interrupt Service Routine (ISR) of the blue push button:

  ```c
  void EXTI15_10_IRQHandler(void)
```
put inside this function the function which trigger the ADC:

  ```c
  HAL_ADC_Start_DMA(&hadc1,(uint32_t *)datiSensori,(uint32_t)NBR_CHANNEL)
```
where 'datiSensori' is the buffer that will contain the converted values, while NBR_CHANNEL represents the number of data to transfer.

At this point all the data are in 'datiSensori' and you can send them through the USART implementing the ADC conversion complete function in mainc.c :

```c
  void HAL_ADC_ConvCpltCallback (ADC_HandleTypeDef * hadc)
  {
    ---
    HAL_UART_Transmit_IT(&huart2, (uint8_t *)string, len);
    ---
  }
  
```

Pay attention that the 'string' variable should contain all the converted numbers in a string format, using the ``` sprintf() ``` function.

At the end you can build the code, upload it and using Putty or the Debug perspective check your work.

 



    
