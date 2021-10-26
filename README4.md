# LAB 5: ADRIÁN ROSAT

(https://github.com/rosatbadia/Digital_Electronics_2)

### 7 SEGMENT LIBRARY

**1. In your words, describe the difference between Common Cathode and Common Anode 7-segment display.**

The MAIN difference between common cathode and common anode is that the first has all the cathodes of the 7-segments connected directly together and to the ground; and the common anode has all the anodes of the 7-segments connected together and to the power supply.

**2. Code listing with syntax highlighting of two interrupt service routines (`TIMER1_OVF_vect`, `TIMER0_OVF_vect`) from counter application with at least two digits, ie. values from 00 to 59:**

ISR(TIMER1_OVF_vect)

 {
 
      DDRD=0xFF;    
      
      DDRB=0xFF;	
        int x, D, U;  //Declare ports and variables
   
   while(1)
   
{  	
	
for (D=0; D<=5; D++) // Accumulate tens 
{

	for (U=0; U<=9; U++)  // Accumulate Units
	{
  
		for (x=0; x<=62; x++)    //Alternate lits
		{
			PORTD=0X00; 
      
			PORTD=n[U]; 
      
			PORTB=0b10000000;  
      
			_delay_ms(2);   
			
			PORTD=0x00;  
      
			PORTD=n[D];  
      
			PORTB=0b01000000;  
      
			_delay_ms(2);   
	  	}
	  }
}


  }
  
  
  **3. Flowchart figure for function `SEG_clk_2us()` which generates one clock period on `SEG_CLK` pin with a duration of 2&nbsp;us. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.**
  ![FLOWCHART](https://user-images.githubusercontent.com/91876413/138861550-bdc49fad-6eab-4de6-83c2-f61aa6503723.png)
  
  
  ### Kitchen alarm

**1. Scheme of kitchen alarm; do not forget the supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values.**


  
![IMAGE (2)](https://user-images.githubusercontent.com/91876413/138861660-f039de72-1ae3-4091-bb59-486a4bca18c7.jpeg)
