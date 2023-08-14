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
![image](https://2700952642-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MClo3nC-1US0rbK8Qau%2Fuploads%2FjDh47ZcPEZxIigyTdjvN%2Fimage.png?alt=media&token=a509413f-9172-47c6-b379-d9aae519eaa2)

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
![image](https://2700952642-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MClo3nC-1US0rbK8Qau%2Fuploads%2Fu1UvN815NDMV6gYNSYLT%2Fimage.png?alt=media&token=43d9a068-49c2-425c-a88a-cc7b5b187cb3)



### Launching the Application      
![image](https://2700952642-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MClo3nC-1US0rbK8Qau%2Fuploads%2F8pmvOcmTss6ShyjsnBEG%2Fimage.png?alt=media&token=83935bea-f354-4985-bebf-d69971f6ea39)

  Note: Before launching the program to the board, make sure that you have already connected the board to the computer through a USB cable.    
  ![image](https://github.com/Advance-Innovation-Centre-AIC/BIIL_MTB-107_Read_potentiometer_sensor_value_via_an_ADC_HAL_Template/assets/88732241/c9966b5b-702f-478e-bbe8-ba9e277800d2)


### Result     
  Once the device is set up, run the program. The microcontroller will continuously read the potentiometer's analog value, convert it to a digital signal through the ADC, and then convert that signal to millivolts using the PDL functions.
![image](https://2700952642-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MClo3nC-1US0rbK8Qau%2Fuploads%2FN4e76IF1ahw2YCVN72i7%2Fimage.png?alt=media&token=8ccebae0-ec96-4c44-9ee8-3669bb7dd0cb)

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

Document title: BILL_MTB-109 – Read potentiometer sensor value via an ADC PDL

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
