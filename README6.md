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
