# BIIL_MTB-109_LED_Brightness_using_PWM_via_PDL_Template

This lab demonstrates the process of controlling LED brightness using PWM via Hardware Abstraction Layer (HAL) on a PSoC 6 microcontroller.
## 🔥 Requirements
| Resources                                  | Links                                                                                                  |
|--------------------------------------------|--------------------------------------------------------------------------------------------------------|
| Computer                                   | 💻                                                                                                    |
| ModusToolbox™ software v3.0 or later       | [Link](https://www.infineon.com/modustoolbox)                                                         |
| CY8CKIT-062S2-43012 Infineon Board         | [Link](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-100_Hello_World_and_LED_Blinking_Programming_Template/assets/88732241/0215501d-b774-4045-8e64-ef49e28d8404) |
| Technical Report | [dropbox](https://www.dropbox.com/scl/fi/amaxc94pte0ut2i1r5ewx/Technical-Report-Lab00.paper?rlkey=b3xm3vrerz9xgv1glb30cvy9z&dl=0)

## 🚩 Let start
### Create Application 
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-108_Read_potentiometer_sensor_value_via_an_ADC_PDL_Template/assets/88732241/9772aa4a-2a04-4e57-bf5b-68444ed1e38d)

### Use Device Configurator and set the UART and ADC pin
#### Enable UART Pin:
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-108_Read_potentiometer_sensor_value_via_an_ADC_PDL_Template/assets/88732241/3c02deae-965c-4ba4-a06c-dfe6de2a206b)
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-108_Read_potentiometer_sensor_value_via_an_ADC_PDL_Template/assets/88732241/a7a53d7d-3bcd-41a3-a7de-f73e0bc8fa23)

##### Config ADC
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-108_Read_potentiometer_sensor_value_via_an_ADC_PDL_Template/assets/88732241/50c27970-64c7-40af-a377-ed3c40eea99f)
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-108_Read_potentiometer_sensor_value_via_an_ADC_PDL_Template/assets/88732241/39e9bd34-81d0-4f23-bde7-f3699df45acf)



### Coding
Coding: Open the main.c file and add the following code to the main(void) function.
```
main.c
int main(void)
{
    cy_rslt_t result;
    cyhal_pwm_t pwm_obj;
​
    /* Initialize the device and board peripherals */
    result = cybsp_init() ;
    if (result != CY_RSLT_SUCCESS){
        CY_ASSERT(0);
    }
​
    __enable_irq();
​
	/* Initialize PWM on the supplied pin and assign a new clock */
    result = cyhal_pwm_init(&pwm_obj, CYBSP_USER_LED, NULL);
​
	/* Start the PWM output */
	result = cyhal_pwm_start(&pwm_obj);
​
	while(true){
		for (int i = 100; i >= 0; i--){
			result = cyhal_pwm_set_duty_cycle(&pwm_obj, i, 10000);
			cyhal_system_delay_ms(10);
		}
	}
}
```
### Build the Application      
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-108_Read_potentiometer_sensor_value_via_an_ADC_PDL_Template/assets/88732241/1763207e-5360-4b37-92cb-14b9263fcf97)



### Launching the Application      
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-108_Read_potentiometer_sensor_value_via_an_ADC_PDL_Template/assets/88732241/247d4903-51d7-47a0-a7c7-dad6bbe53920)

  Note: Before launching the program to the board, make sure that you have already connected the board to the computer through a USB cable.    
  ![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-107_Read_potentiometer_sensor_value_via_an_ADC_HAL_Template/assets/88732241/c9966b5b-702f-478e-bbe8-ba9e277800d2)


### Result     
  Once the device is set up, run the program. The microcontroller will continuously read the potentiometer's analog value, convert it to a digital signal through the ADC, and then convert that signal to millivolts using the PDL functions.
![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-108_Read_potentiometer_sensor_value_via_an_ADC_PDL_Template/assets/88732241/73fc9907-773d-4f9d-8137-8aa1ca84ddbd)

### 🎉  Congratulations! You can now complete Lab108

## Supported toolchains (make variable 'TOOLCHAIN')

- GNU Arm&reg; embedded compiler v10.3.1 (`GCC_ARM`) - Default value of `TOOLCHAIN`
- Arm&reg; compiler v6.16 (`ARM`)
- IAR C/C++ compiler v9.30.1 (`IAR`)

## Supported kits (make variable 'TARGET')

- [PSoC&trade; 62S2 Wi-Fi Bluetooth&reg; pioneer kit](https://www.infineon.com/CY8CKIT-062S2-43012) (`CY8CKIT-062S2-43012`)
- [PSoC&trade; 62S1 Wi-Fi Bluetooth&reg; pioneer kit](https://www.infineon.com/CYW9P62S1-43438EVB-01) (`CYW9P62S1-43438EVB-01`)
- [PSoC&trade; 62S1 Wi-Fi Bluetooth&reg; pioneer kit](https://www.infineon.com/CYW9P62S1-43012EVB-01) (`CYW9P62S1-43012EVB-01`)
- [PSoC&trade; 62S3 Wi-Fi Bluetooth&reg; prototyping kit](https://www.infineon.com/CY8CPROTO-062S3-4343W) (`CY8CPROTO-062S3-4343W`)


## Related resources
Resources  | Links
-----------|----------------------------------
ModusToolbox™ Software Training | [link](https://www.dropbox.com/sh/waj898o4o8eccx0/AAB3hBBaIQo2OvJ5-fubGJIha/training-modustoolbox-level1-getting-started-master/Manual/Ch2-Tools.pdf?dl=0)

## Other resources

Infineon provides a wealth of data at www.infineon.com to help you select the right device, and quickly and effectively integrate it into your design.


## Document history

Document title: BILL_MTB-108 – Read potentiometer sensor value via an ADC PDL

 Version | Description of change
 ------- | ---------------------
 1.0.0   | Lab 108: Learn basic GPIO control with PSoC 6, using ADC read potentiometer sensor value via PDL

## Authors:
- *Assoc. Prof. Wiroon Sriborrirux*
- *Mr. Sriengchhun Chheang*
- *Mr. Sabol Socare*
<br>

<br>

---------------------------------------------------------

© BDH Corporation, 2022-2023