# LAB 4: ADRIAN ROSAT BADIA

(https://github.com/rosatbadia/Digital_Electronics_2)

## Overflow times ##

**1. Complete table with overflow times**

| **Module** | **Number of bits** | **1** | **8** | **32** | **64** | **128** | **256** | **1024** |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| Timer/Counter0 | 8  | 16u | 128u | -- | 1024u | -- | 4096u |16384u |
| Timer/Counter1 | 16 | 4096u    |  32768u   | -- | 262144u | -- |1048576u | 4194304u |
| Timer/Counter2 | 8  | 16u    | 128u     |  512u  | 1024u |  2048u  |4096u | 16384u|

## Timer library

1. In your words, describe the difference between common C function and interrupt service routine.
   
   The Interrupt Service Routine (ISR) it is a signal to the processor emitted by hardware or software indicating an event that needs immediate attention. When there is an interrupt, the program finishes the task which is already doing and then starts the interrupt instruction. After the execution of ISR, the processor must resume to program exactly as before the interrupt occurred.
   Besides, the interrupt is usually initiated by an internal or a external signal microprocessor rather than the execution of instructions. On the other hand, when we have a function, its address of the subroutine is written inside the instructions which is written in the main program code. 

2. Part of the header file listing with syntax highlighting, which defines settings for Timer/Counter0:

  #ifndef TIMER_H
   
  #define TIMER_H


  #include <avr/io.h>

 
#define TIM0_stop()             TCCR0B &= ~((1<<CS12) | (1<<CS11) | (1<<CS10));         // 000 --> STOP

#define TIM0_overflow_16us()     TCCR0B &= ~((1<<CS12) | (1<<CS11)); TCCR0B |= (1<<CS10);// 001 --> 1

#define TIM0_overflow_128us()    TCCR0B &= ~((1<<CS12) | (1<<CS10)); TCCR0B |= (1<<CS11);// 010 --> 8

#define TIM0_overflow_1024us()   TCCR0B &= ~(1<<CS12); TCCR0B |= (1<<CS11) | (1<<CS10);  // 011 --> 64

#define TIM0_overflow_4ms()      TCCR0B &= ~((1<<CS11) | (1<<CS10)); TCCR0B |= (1<<CS12);// 100 --> 256

#define TIM0_overflow_16ms()      TCCR0B &= ~(1<<CS11); TCCR0B |= (1<<CS12) | (1<<CS10);  // 101 --> 1024

#define TIM0_overflow_interrupt_enable()    TIMSK0 |= (1<<TOIE0);   // 1 --> enable

#define TIM0_overflow_interrupt_disable()   TIMSK0 &= ~(1<<TOIE0);  // 0 --> disable

#endif


3. Flowchart figure for function main() and interrupt service routine ISR(TIMER1_OVF_vect) of application that ensures the flashing of one LED in the timer interruption. When the button is pressed, the blinking is faster, when the button is released, it is slower. Use only a timer overflow and not a delay library. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.


![diagram](https://user-images.githubusercontent.com/91876413/137890379-b1940e64-acee-441f-a19e-2b3345172417.jpeg)


## KNIGHT RIDER

1. Scheme of Knight Rider application with four LEDs and a push button, connected according to Multi-function shield. Connect AVR device, LEDs, resistors, push button, and supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values

![atmega328](https://user-images.githubusercontent.com/91876413/137890520-8f230295-d9c3-4e7a-958b-eef9051ed19d.jpeg)







