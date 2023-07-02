# STM32F103C8T6_LM35_DMA
## Author: Harry Nguyen (Created 07/01/2023)

This is my new project during my self-study of STM32 ARM MCU, to implement my knowledge of ADC module to interface with the LM35 temperature sensor using the HAL library. However, instead of normally polling for the ADC conversion result, I have decided to decrease the CPU load as much as possible using the timer trigger and the special DMA controller of the ARM cortex, which is a great feature to deal with RTOS system.

### Components:
- STM32F103C8T6 Blue Pill
- LM35 temperature sensor
- Power supply
- UART-TTL chip

To interface with the LM35 sensor, please refer to the datasheet of the manufacturer. In this project, I only configure the system to read the positive temperature value, however, to read the negative temperature, we must use at least 2 ADC channel, and use another connection circuit.

### Notes:
- Please notice to configure the DMA mode to circular, so that the ADC conversion continuously. I stucked at this point for at least a day :((
- Notice the order of configuring different module, the HAL_TIM_Base_Start must be right before the HAL_ADC_Start_DMA, and the function DMA_Init must be called before the TIM_Init, or the DMA position will be misleaded.

## References:
1. Khaleg Magdy, STM32 ARM tutorial series, https://deepbluembedded.com/stm32-lm35-temperature-sensor-example-lm35-with-stm32-adc/.
2. Blima.1, TIMER + ADC + DMA, https://community.st.com/t5/stm32cubemx-mcu/timer-adc-dma/td-p/77703.
3. Bart Slinger, STM32 CubeMX “Timer + ADC + DMA”, https://www.bartslinger.com/stm32/stm32-cubemx-timer-adc-dma-configuration/.


