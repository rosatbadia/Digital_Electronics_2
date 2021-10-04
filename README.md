# Digital-Electronics-2


(https://github.com/rosatbadia/Digital_Electronics_2)

# Lab1 


**1. What is the meaning of the following binary operators in C?**

    1.1. | :means bit to bit OR
    
    1.2. & :means bit to bit AND
    
    1.3. ^ :means XOR, Exclusive or![image](https://user-images.githubusercontent.com/91876413/135858935-1a0a57be-ca2f-4999-b511-1b7e5f4566da.jpeg)


    1.4. ~ :means Complement to one or bit to bit negation 

    1.5. << :means move to left

    1.6. >> :means move to right

**2.Complete truth table with operators: | ,  & , ^ ,~ ,**

b   |    a   |  b or a | b and a |  b xor a | not b |
----|--------|---------|---------|----------|-------|
0   |    0   |    0    |    0    |    0     |   1   |
0   |    1   |    1    |    0    |    1     |   1   |
1   |    0   |    1    |    0    |    1     |   0   |
1   |    1   |    1    |    1    |    0     |   0   |


**3. Morse code**

*I'm going to write "HELLO"*

    CODE:
#define SHORT_DELAY 50ms

    int main(void)
    {
        // Set pin as output in Data Direction Register
        // DDRB = DDRB or 0010 0000
        DDRB = DDRB | (1<<LED_GREEN);

        // Set pin LOW in Data Register (LED off)
        // PORTB = PORTB and 1101 1111
        PORTB = PORTB & ~(1<<LED_GREEN);

        // Infinite loop
        while (1)
        {
            // Pause several milliseconds
            _delay_ms(SHORT_DELAY);

            // WRITE YOUR CODE HERE
            // LETTER H
            DDRB = DDRB | (1<<LED_GREEN);
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
             DDRB = DDRB | (1<<LED_GREEN);
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
             DDRB = DDRB | (1<<LED_GREEN);
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
             DDRB = DDRB | (1<<LED_GREEN);
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
            
            // I have put 4 dalays to separate each point of the morse code and see it better in the LED
            // LETTER E:
             DDRB = DDRB | (1<<LED_GREEN);
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
            
            //LETTER L:
            int i;
            for (i=0, i<2, i++){  //I do a for loop because the L is repeated 2 times
             DDRB = DDRB | (1<<LED_GREEN);
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
             DDRB = DDRB | (1<<LED_GREEN);
             _delay_ms(SHORT_DELAY); // I mantain the LED on because it's a long stripe
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
             DDRB = DDRB | (1<<LED_GREEN);
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
             DDRB = DDRB | (1<<LED_GREEN);
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
            }
         
            
            //LETTER O:
            DDRB = DDRB | (1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
            DDRB = DDRB | (1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
            DDRB = DDRB | (1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
            PORTB = PORTB & ~(1<<LED_GREEN);
            _delay_ms(SHORT_DELAY);
           
        }

        // Will never reach this![image]

        return 0;
    }
    
    
    
    
    

![image](https://user-images.githubusercontent.com/91876413/135898304-0289b664-b4bd-47da-b295-4fa82b7e9e87.jpeg)
