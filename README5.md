# Lab 6: ADRIAN ROSAT

(https://github.com/rosatbadia/Digital_Electronics_2)


### LCD display module

**1. In your words, describe what ASCII table is.**

   * ASCII: The ASCII table contains letters, numbers, control characters, and other symbols. Each character is assigned a unique 7-bit code. When you write in ASCII code you can write the character directly between simple commas, or you can write the number that represent that character, in decimal, hexadecimal, or binary
            The purpose of ASCII is to create a standard for character-sets used in electronic equipments
            
**2. (Hand-drawn) picture of time signals between ATmega328P and LCD keypad shield (HD44780 driver) when transmitting three character data `De2`**

![scaned picture](https://user-images.githubusercontent.com/91876413/139718659-d9e60e90-6503-4301-b94f-aa93492ceafb.jpeg)



### Stopwatch

**1. Flowchart figure for `TIMER2_OVF_vect` interrupt service routine which overflows every 16&nbsp;ms but it updates the stopwatch LCD approximately every 100&nbsp;ms (6 x 16&nbsp;ms = 100&nbsp;ms). Display tenths of a second and seconds `00:seconds.tenths`. Let the stopwatch counts from `00:00.0` to `00:59.9` and then starts again. The image can be drawn on a computer or by hand. Use clear descriptions of the individual steps of the algorithms.**

![flowchart3](https://user-images.githubusercontent.com/91876413/139716942-24095a5e-81bc-45ce-afbe-cefd72aab4c4.png)

### Custom characters

**1. Code listing with syntax highlighting of two custom character definition:**

/* Variables ---------------------------------------------------------*/

// Custom character definition

//I'm going to write: ET

uint8_t customChar[16] = {

  0b11111,
  
	0b10000,
  
	0b10000,
  
	0b10000,
  
	0b11111,
  
	0b10000,
  
	0b10000,
  
	0b11111,
  
  0b11111,
  
	0b00100,
  
	0b00100,
  
	0b00100,
  
	0b00100,
  
	0b00100,
  
	0b00100,

	0b00100,

};

### Kitchen alarm

**1. Scheme of kitchen alarm; do not forget the supply voltage. The image can be drawn on a computer or by hand. Always name all components and their values.**
