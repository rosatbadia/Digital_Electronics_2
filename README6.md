# Lab 7: ADRIAN ROSAT 

(https://github.com/rosatbadia/Digital_Electronics_2)

### Analog-to-Digital Conversion

**1.Complete table with voltage divider, calculated, and measured ADC values for all five push buttons**

   | **Push button** | **PC0[A0] voltage** | **ADC value (calculated)** | **ADC value (measured)** |
   | :-: | :-: | :-: | :-: |
   | Right  | 0&nbsp;V | 0   |  |
   | Up     | 0.495&nbsp;V | 101.27 |  |
   | Down   | 0.784&nbsp;V | 160.4  |  |
   | Left   | 1.01&nbsp;V  | 206.64 |  |
   | Select | 2&nbsp;V     | 409.2  |  |
   | none   |  5&nbsp;V    | 1023   |  |
   
 **2. Code listing of ACD interrupt service routine for sending data to the LCD/UART and identification of the pressed button. Always use syntax highlighting and meaningful comments:**

```c
/**********************************************************************
 * Function: ADC complete interrupt
 * Purpose:  Display value on LCD and send it to UART.
 **********************************************************************/
ISR(ADC_vect)
{
    uint16_t value = 0;
    char lcd_string[4] = "0000";

    value = ADC;                  // Copy ADC result to 16-bit variable
    itoa(value, lcd_string, 10);  // Convert decimal value to string

    // WRITE YOUR CODE HERE

}
```

### UART communication

**1. (Hand-drawn) picture of UART signal when transmitting three character data `De2` in 4800 7O2 mode (7 data bits, odd parity, 2 stop bits, 4800&nbsp;Bd).**

![imaage](https://user-images.githubusercontent.com/91876413/140769419-a414ab92-a9a9-4f74-9241-d6f76d0bf780.jpeg)

**2. Flowchart figure for function `uint8_t get_parity(uint8_t data, uint8_t type)` which calculates a parity bit of input 8-bit `data` according to parameter `type`. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.**

![flowchart parity](https://user-images.githubusercontent.com/91876413/140780580-5815f56f-3510-471a-93ad-367b8bb2f026.png)



### Temperature meter

**1. Scheme of temperature meter. The image can be drawn on a computer or by hand. Always name all components and their values.**


