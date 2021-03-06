# Lab 7: ADRIAN ROSAT 

(https://github.com/rosatbadia/Digital_Electronics_2)

### Analog-to-Digital Conversion

**1.Complete table with voltage divider, calculated, and measured ADC values for all five push buttons**

   | **Push button** | **PC0[A0] voltage** | **ADC value (calculated)** | **ADC value (measured)** |
   | :-: | :-: | :-: | :-: |
   | Right  | 0&nbsp;V | 0   |  |
   | Up     | 0.495&nbsp;V | 101.27 | 100-101 |
   | Down   | 0.784&nbsp;V | 160.4  | 159-160 |
   | Left   | 1.01&nbsp;V  | 206.64 | 206-207 |
   | Select | 2&nbsp;V     | 409.2  | 408-409 |
   | none   |  5&nbsp;V    | 1023   | 1023-1024 |
   
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
    
    // Initialize LCD display
    lcd_init(LCD_DISP_ON);
    lcd_gotoxy(0, 1);

    switch (lcd_key)               // depending on which button was pushed, we perform an action
  {
  case btnRIGHT:
    {
      lcd_puts("RIGHT ");
      break;
    }
  case btnLEFT:
    {
      lcd_puts("LEFT   ");
      break;
    }
  case btnUP:
    {
      lcd_puts("UP    ");
      break;
    }
  case btnDOWN:
    {
      lcd_puts("DOWN  ");
      break;
    }
  case btnSELECT:
    {
      lcd_puts("SELECT");
      break;
    }
  case btnNONE:
    {
      lcd_puts("NONE  ");
      break;
    }
  }

}


int read_LCD_buttons()
{
  adc_key_in = analogRead(0);      // read the value from the sensor 
  delay(5); //switch debounce delay
  int k = (analogRead(0) - adc_key_in); 
  if (5 < abs(k)) return btnNONE;  // double checks the keypress
  
  if (adc_key_in > 1023) return btnNONE; 
  if (adc_key_in < 100)   return btnRIGHT;  
  if (adc_key_in < 159)  return btnUP; 
  if (adc_key_in < 206)  return btnDOWN; 
  if (adc_key_in < 408)  return btnLEFT; 
  if (adc_key_in < 1023)  return btnSELECT;   
  return btnNONE;  // when all others fail, return this...
}


}
```

### UART communication

**1. (Hand-drawn) picture of UART signal when transmitting three character data `De2` in 4800 7O2 mode (7 data bits, odd parity, 2 stop bits, 4800&nbsp;Bd).**

![imaage](https://user-images.githubusercontent.com/91876413/140769419-a414ab92-a9a9-4f74-9241-d6f76d0bf780.jpeg)

**2. Flowchart figure for function `uint8_t get_parity(uint8_t data, uint8_t type)` which calculates a parity bit of input 8-bit `data` according to parameter `type`. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.**

![flowchart parity](https://user-images.githubusercontent.com/91876413/140780580-5815f56f-3510-471a-93ad-367b8bb2f026.png)



### Temperature meter

**1. Scheme of temperature meter. The image can be drawn on a computer or by hand. Always name all components and their values.**


![scheme lcd](https://user-images.githubusercontent.com/91876413/140788254-769f2c65-ac5f-43d7-b9d8-0e6f99703d7a.jpeg)
