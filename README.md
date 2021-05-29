# stm32f4-SRAM-tester

<h1>Description:</h1>

This is a simple STM32F429 program that can be used to test 32K SRAM ICs(61256/62256 for example) and see if they are capable of holding values written to them. The motivation for this project was testing L1 cache chips found on old motherboards.

The program uses the GPIO pins of the F429 to communicate with the SRAM chip. Shift registers weren't used as the F429 has a lot of GPIO pins. The program writes 0xAA to even addresses, 0xBB to odd addresses that are divisible by three and 0X55 to the remaining addresses. The program then verifies the pattern using the addresses and counts mismatches(if there are any). 

This only checks if the SRAM chips is capable of holding values at all and doesn't perform more elaborate tests like RAM testing programs such as memtest86 but more tests might be added in the future. Despite the simplicity of the program, it has been successful at testing old (20+ years) chips. 

<h1>Connection Table:</h1>

*STM32F429* | *SRAM(61256)*
------------ | -------------
PB[0-7] | IO[1-8]
PB[8-15] | A[0-7]
PE[2-8] | A[8-14]
PE9 | WE
PE10 | OE

The chip enable pin of the SRAM is connected to GND as the chip doesn't need to be disabled in this scenario. 

<h1>TODO:</h1>

- Add a zero fill test
- Add a one fill test
- Add a multiple pass random number test
