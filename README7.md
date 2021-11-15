# Lab 8: ADRIÁN ROSAT

https://github.com/rosatbadia/Digital_Electronics_2/tree/main/%7BLabs%7D

### Arduino Uno pinout

**1. In the picture of the Arduino Uno board, mark the pins that can be used for the following functions:**



  ![arduino_uno_pinout](https://user-images.githubusercontent.com/91876413/141693939-74ed1589-7576-477a-8532-f8d48e5e0408.png)


### I2C

**1. Code listing of Timer1 overflow interrupt service routine for scanning I2C devices and rendering a clear table on the UART. Always use syntax highlighting and meaningful comments:**

```c
/**********************************************************************
 * Function: Timer/Counter1 overflow interrupt
 * Purpose:  Update Finite State Machine and test I2C slave addresses 
 *           between 8 and 119.
 **********************************************************************/
ISR(TIMER1_OVF_vect)
{
    static state_t state = STATE_IDLE;  // Current state of the FSM
    static uint8_t addr = 7;            // I2C slave address
    uint8_t result = 1;                 // ACK result from the bus
    char uart_string[2] = "00"; // String for converting numbers by itoa()

    // FSM
    switch (state)
    {
    // Increment I2C slave address
    case STATE_IDLE:
        addr++;
        
        // If slave address is between 8 and 119 then move to SEND state
                if (addr > 7 && addr < 120)
                    state = STATA_SEND;
                if ( addr > 120){
                    uart_puts_P("\r\nScan I2C-bus for devices:\r\n");
                    addr = 0;
                }
        break;
    
    // Transmit I2C slave address and get result
    case STATE_SEND:
        // I2C address frame:
        // +------------------------+------------+
        // |      from Master       | from Slave |
        // +------------------------+------------+
        // | 7  6  5  4  3  2  1  0 |     ACK    |
        // |a6 a5 a4 a3 a2 a1 a0 R/W|   result   |
        // +------------------------+------------+
        result = twi_start((addr<<1) + TWI_WRITE);
        twi_stop();
        /* Test result from I2C bus. If it is 0 then move to ACK state, 
         * otherwise move to IDLE */

        break;

    // A module connected to the bus was found
    case STATE_ACK:
        // Send info about active I2C slave to UART and move to IDLE
        itoa(addr, uart_string, 10);
        uart_puts_P("Found device at adress: ");
        uart_puts(uart_string);
        uart_puts_P("\r\n");
        state = STATE_IDLE;
        
        break;

    // If something unexpected happens then move to IDLE
    default:
        state = STATE_IDLE;
        break;
    }
}









```

**2. (Hand-drawn) picture of I2C signals when reading checksum (only 1 byte) from DHT12 sensor. Indicate which specific moments control the data line master and which slave.**
![simulide lab8](https://user-images.githubusercontent.com/91876413/141791144-82e53207-c0cb-4349-874b-9239465e1add.jpeg)


