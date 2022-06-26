Program Analysis Activities

How many times do the LEDs flash if SW2 is quickly pressed and released? Do the LEDs keep flashing when SW2 is held? Look at the program and explain why this happens when SW2 is held.

The LEDs flash once in a circle when it is quickly pressed and released. The LEDs do keep flashing when SW2 is held. This happens because it is in a while loop where the code runs repeatedly.

Explain the difference between the statements: LED3 = 0; and LED3 = 1;

The difference between the statements LED3 = 0 and LED3 = 1 is that when LED3 is equal to 0, nothing will happen which means that the LED3 will not flash. However, when LED3 is equal to 0, LED3 lights up.

What voltage do you expect the microcontroller to output to LED D3 when the statement LED3 = 0; runs? What voltage do you expect the output to be when the statement LED3 = 1; runs? 

When LED3 = 0 runs, I expect the voltage to be 0 volts. When LED3 = 1 runs, I expect the voltage to be 2.3 volts.

You can confirm the output voltage with a voltmeter if you have access to one. If you tried that, did the voltage match your prediction?

It did match my prediction.

The statement 'if(SW2 == 0)' uses two equal signs, while the statement ‘'LED3 = 1;' uses a single equal sign. What operation is performed by one equal sign? What operation is performed by two equal signs?

One equal sign assigns a task whereas two equals signs means if ‘a’ is equivalent to ‘b’.

The following program code includes instructions that write to the PORTC output latches directly. Try it by copying and pasting this code below the existing SW2 'if' structure, at the location shown by the comment.

if(SW3 == 0)
{
LATC = 0b00000000;
            __delay_ms(100);
            LATC = 0b11110000;
            __delay_ms(100);
}

What happens when pushbutton SW3 is pressed? Identify at least one advantage and one disadvantage of controlling the LEDs using 'LATC' writes rather than through individual 'LEDn = x;' statements.

When SW3 is pressed, all the yellow LEDs flash and light up. An advantage of controlling the LEDs using ‘LATC’ is that you don't have to code for each individual LED. A disadvantage would be that you would have to know each code for each LED.

Next, compare the operation of 'if' and 'while' structures to simulate momentary buttons. Replace the code you added in 5, above, with this code:

// Momentary button using if structure
        if(SW3 == 0)
        {
            LED4 = 1;
        }
        else
        {
            LED4 = 0;
        }

        // Momentary button using while structure
        while(SW4 == 0)
        {
            LED5 = 1;
        }
        LED5 = 0;

First, try pressing and releasing SW3 and SW4 one at a time. Next, press and hold SW3 while pressing and releasing SW4. Does it work as expected?

Yes, it does work as expected.

Next, try press and holding SW4 while pressing and releasing SW3. Does it work as expected? 

Yes, it does work as expected.

Explain the difference in operation between the 'if' and 'while' structures making up the momentary button code.

The difference between the ‘if’ and ‘while’ structures is that if LED4 is pressed, light up the LED. For the ‘while’ structure, while LED4 is pressed, you can press LED5 which will light up with LED4.
Let's explore logical conditions using 'if' statements. Replace the code added in 6, above, with this nested if code to make a logical AND condition that will light LED D4 only if both SW3 and SW4 are pressed:
 
       // Nested if 'AND' code
       if(SW3 == 0)
       {
           if(SW4 == 0)
           {
               LED4 = 1;
           }
           else
           {
               LED4 = 0;
           }
       }
       else
       {
           LED4 = 0;
       }
 
Test the code to ensure it works as expected. Does the order of the if conditions matter? (eg. swap the conditional checks for SW3 and SW4)
 
No, the order does not matter.
 
Next, replace the code from 7 with the following code which implements a logical AND conditional operator composed of two ampersands '&&':
       // Conditional 'AND' code
       if(SW3 == 0 && SW4 == 0)
       {
           LED4 = 1;
       }
       else
       {
           LED4 = 0;
       }
 
Does '&&' work the same way as the nested if structures? Can you think of at least one advantage of using a logical conditional operator instead of nested if structures?
 
No, it does not work the same way as the nested ‘if’ structures. An advantage of using a logical conditional operator instead of nested ‘if’ structures would be that a logical conditional operator uses one ‘if’ statement whereas the nested ‘if’ structures uses two ‘if’ statements.
 
Replace the double ampersand '&&' with double vertical bars '||)' to make a logical OR conditional operator. Your code should look like this:
        // Conditional 'OR' code
       if(SW3 == 0 || SW4 == 0)
       {
           LED4 = 1;
       }
       else
       {
           LED4 = 0;
       }
 
Describe the conditions under which LED4 turns on.
 
When SW4 is pressed, LED4 lights up.
When SW3 is pressed, LED4 lights up.
When SW3 and SW4 are pressed, LED4 lights up and will stay lit up if SW4 is let go and SW3 is still pressed.
 
 
 
 
 
 
Programming Activities
The statement '__delay_ms(100);' creates a 100ms delay. Try changing one or more of the delay values in the program to 500ms and see what happens.
 
Can the delay be made even longer? Try 1000 ms. How big can the delay be before MPLAB-X produces an error message? (Hint: can you think of a fast and efficient way of guessing an unknown number?)
Beepers pitch increases as the value for the delay decreases. The max value is 4205 ms.
 
The '__delay_ms();' function only accepts integers as delay values. To make delays shorter than 1ms, specify a delay in microseconds using the '__delay_us();' function. You won't be able to see such short LED flashes with your eyes, but you could measure them using an oscilloscope, or hear them if they are used to turn the piezo beeper on and off. Try this code:
 
       // Make a tone while SW5 is held
       if(SW5 == 0)
       {
           BEEPER = 1;
           __delay_us(567);
           BEEPER = 0;
           __delay_us(567);
       }
 
Try changing the delay values in both of the __delay_us(); functions. Does the pitch of the tone increase or decrease if the delay value is made smaller?
 
The pitch increases the tone when the delay value is lower than 567.
 
This code demonstrates a more compact way of toggling the beeper output using a logical NOT operator '!'. Replace the code above, with this code:
       // Make a tone while SW5 is held
       if(SW5 == 0)
       {
           BEEPER = !BEEPER;
           __delay_us(567);
       }
 
One difference between this code and the code in 2, above, is the state of the BEEPER pin when SW5 is released. What state will the BEEPER output be in after this code runs? While one advantage of this method is smaller code, can you think of one or more disadvantages based on its output when the button is released?
 
Another disadvantage, the state of the beeper will be unknown once the button is released.
 
Using modified versions of the original SW2 'if' structure, create a program that makes a unique LED flashing pattern for each pushbutton. Test each of your flashing patterns. Describe what happens when more than one button is held. Do all of the patterns try to flash the LEDs at the same time, or sequentially? Explain why this is.
 
Multiple tones are on top of each other.
 
Create a program that makes a different tone for each pushbutton. Test each tone by pressing each button individually. Next, press two or more buttons at the same time. Describe what the tone waveform would look like when more than one button is held.
 
The waveforms would either be in a higher or lower pitch sound.
 
Use individual 'if' structures to simulate 'Start' and 'Stop' buttons for an industrial machine. LED D4 should turn on when SW3 is pressed, stay on even after SW3 is released, and turn off when SW4 is pressed. Test your program to make sure it works.
 
if(SW3 == 0)
	{
		LED5 = 1;
	}
 
	if(SW4 == 0)
	{
		LED5 = 0;
	}
 
Running your program from 6, above, describe what happens when both SW3 and SW4 are pressed. Does LED D4 stay on? If so, how does the brightness of LED D4 compare between its normal state following SW3 being pressed to this new state when both SW3 and SW4 are being held? Can you explain why it changes?
 
As the LED brightness dims, SW4 is decreasing power while SW3 is supplying power to the LED.
 
As you can imagine, an industrial machine that is able to turn on even while its 'Stop' button is pressed represents a significant safety hazard. Using a logical conditional operator, modify the start-stop program from activity 5 to make it safer. SW3 should only turn on LED D4 if SW4 is released.
 
while(SW4 == 1) 
{
if(SW3 == 0)
{
LED4 = 1;
} 
} 
 
if(SW4 ==0)
{
LED4 = 0;
}
 
 
LED D1 is normally used to indicate that a program is running, but it can be controlled by your program as well. If you take a look at the UBMP4 schematic, you will see that LED D1's cathode (or negative) pin is connected to the microcontroller instead of the anode (positive) pin as with the other LEDs. This means that you need to make D1's output a zero to turn D1 on. Try it! Make a program that controls or flashes LED D1.
 
if(SW3 == 0) 
{
LED1 = 0;
__delay_ms(50);
LED1 = 1;
 __delay_ms(50);
	}
