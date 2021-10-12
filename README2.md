# LAB 3: ADRIÁN ROSAT

(https://github.com/rosatbadia/Digital_Electronics_2)

  ## DATA TYPES IN C ##

**1. Complete table**

| **Data type** | **Number of bits** | **Range** | **Description** |
| :-: | :-: | :-: | :-- | 
| `uint8_t`  | 8 | 0, 1, ..., 255 | Unsigned 8-bit integer |
| `int8_t`   | 8 | 0, 1, ..., 127 | Signed 8-bit integer |
| `uint16_t` | 16 | 0, 1, ...,  65535 | Unsigned 16-bit integer |
| `int16_t`  | 16 | 0, 1, ..., 32767  | Signed 16-bit integer |
| `float`    |  | -3.4e+38, ..., 3.4e+38 | Single-precision floating-point |
| `void`     |  |  | Void means without any value. Does not return anything|

  ## GPIO LIBRARY ##
  
  **1. In your words, describe the difference between the declaration and the definition of the function in C**
  
  The main diference is that in the function declaration you only specify the function and return type, its name and the parameters you are going to use. You usually declare it in the part of the code where there are other declarations.
  On the other hand , there is the function definition, which includes all the things declarated before and the body of the function, where you wrtite all the things you want to do or calculate to return them.
  It's like, the declaration is the creation of a new function, and the definition is the explaining and things that do that function (the body).
  
  **2. Part of the C code listing with syntax highlighting, which toggles LEDs only if push button is pressed. Otherwise, the value of the LEDs does not change. Use function from your GPIO library. Let the push button is connected to port D:**

CODE:

#define LED_GREEN PB5

#define BLINK_DELAY 500

#indef F_CPU

#define F_CPU 16000000

#endif

#include <avr/io.h>

#include "gpio.h"

#include <until/delay.h>

int main (void)
{

  GPIO_config_output (&DDBR, LED_GREEN);
  
  GPIO_write_low (&PORT; LED_GREEN);
  
  GPIO_config_input_nopullup (volatile uint8_t *LED2, uint8_t PORTC)
  
  GPIO_config_input_nopullup (volatile uint8_t *PUSH_BUTTON, uint8_t PORTD)
  
  while(1)
  {
    _delay_ms (BLINK_DELAY);
    
    }
 }
    




## TRAFFIC LIGHT ##

**1. Scheme of traffic light application with one red/yellow/green light for cars and one red/green light for pedestrians. Connect AVR device, LEDs, resistors, one push button (for pedestrians), and supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values!**![image2](https://user-images.githubusercontent.com/91876413/136817738-36af1262-64b9-41b4-9173-53fbb1f98ef4.jpeg)



