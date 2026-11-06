# Circuit Project 2: Seven-Segment Display Decimal Adder
- CSCE 211H: Digital Logic Design

- Katie Kilborn, Jose Felton, Wyatt Bowen

This project implements a decimal adder. It accepts two 4 bit operands and displays the result using a four seven segment display. The sum is displayed using the tens and ones digits. We used two four way multiplexers to select the two four bit operands. The operands are then send to the adder.

## Four Bit Adder Implementation
| A | B | Cin | S | Cout |
|:---:|:---:|:---:|:---:|:---:|
| 0 | 0 | 0 | 0 | 0 | 
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 | 
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

S = A'B'Cin + A'BCin' + AB'Cin' + ABCin

Cout = A'BCin + AB'Cin + ABCin' + ABCin

This truth table was created by putting the binary version of number 0-7 for A, B, and Cin. S and Cout represent those input values added together where S is the ones bit of the result and Cout is the carry value. The sum of minterms expressions were then able to be put together for S and Cout by putting every value of each output into its expression to create the final sum of minterms expression for the four bit adder. 
This adder was implemented using four full adders connected together using the expressions listed above where each full adder receives the Cout value from the previous adder and the first adder starts with 0 as it's Cin value. With the final adder, S is outputted as the sum. 

## Sum Display Conversion Table
| Binary Sum | Tens | Ones |
|:---:|:---:|:---:|
| 0000 | 0 | 0 | 
| 0001 | 0 | 1 |
| 0010 | 0 | 2 |
| 0011 | 0 | 3 |
| 0100 | 0 | 4 |
| 0101 | 0 | 5 | 
| 0110 | 0 | 6 |
| 0111 | 0 | 7 |
| 1000 | 0 | 8 |
| 1001 | 0 | 9 |
| 1010 | 1 | 0 |
| 1011 | 1 | 1 |
| 1100 | 1 | 2 |
| 1101 | 1 | 3 |
| 1110 | 1 | 4 |
| 1111 | 1 | 5 |
| 10000 | 1 | 6 |
| 10001 | 1 | 7 |
| 10010 | 1 | 8 |

The sum from the adder ranges from 0-18 and so we had to display the binary number we received in decimal. The sum is sent to the double-dabble circuit which converts the binary into two BCD digits. Those digits represent the ones and the tens place. The digits are converted in the display drivers to properly light up the segments for displaying the sum. 
