# ardATProgrammer

Some code and a shield for programming ATMega328 and ATtiny85

## Additional Boards Managers URL

Insert these URLs in File -> Preferences -> Settings tab  

>damellis: [https://raw.githubusercontent.com/damellis/attiny/ide-1.6.x-boards-manager/package_damellis_attiny_index.json](https://raw.githubusercontent.com/damellis/attiny/ide-1.6.x-boards-manager/package_damellis_attiny_index.json)  
>leonardomilliani: [http://www.leonardomiliani.com/repository/package_leonardomiliani.com_index.json](http://www.leonardomiliani.com/repository/package_leonardomiliani.com_index.json)  
>carlosefr: [https://raw.githubusercontent.com/carlosefr/atmega/master/package_carlosefr_atmega_index.json](https://raw.githubusercontent.com/carlosefr/atmega/master/package_carlosefr_atmega_index.json)  

Then install boards in Tools -> Board -> Boards manager...  

>attiny  
>ATtiny extra Boards  
>ATmega 168P/328P Boards  
>Barebones ATmega Chips (no bootloader)  

## Burn bootloader, settings

### ATtiny85

Board -> ATtiny Microcontrollers -> ATtiny 25/45/85  
Processor -> ATtiny85  
Clock -> ...  
Programmer -> Arduino as ISP  

### ATtiny2313

Board -> ATtiny MCUs -> ATtiny2313/4313  
Micro -> ATtiny2313 @ ...  
Programmer -> Arduino as ISP

### ATmega328P

Board -> Arduino AVR Boards -> Arduino Duemilanove or or Diecimila  
Processor -> ATmega 328P  
Programmer -> Arduino as AVR  

or  

Board -> Atmega168/328 -> Atmega168/328  
Micro -> ATmega328P @ ... w/Arduino as ISP  

### ATmega328

No solution to burn bootloader at the moment  

## Program AVR, settings

### ATtiny85

Board -> ATtiny Microcontrollers -> ATtiny 25/45/85  
Processor -> ATtiny85  
Clock -> ...  
Programmer -> Arduino as ISP

### ATtiny2313

Board -> ATtiny MCUs -> ATtiny2313/4313  
Micro -> ATtiny2313 @ ...  
Programmer -> Arduino as ISP

### ATmega328P

Board -> Atmega168/328 -> Atmega168/328  
Micro -> ATmega328P @ ... w/Arduino as ISP

### ATmega328

Board -> ATmega Microcontrollers -> ATmega328/328P  
Processor -> ATmega328  
Clock -> ...  
Programmer -> Arduino as ISP

## Pin Mapping, Arduino IDE -> AVR

### Arduino code -> ATtiny85 pin number -> Pin name -> Function

0 -> 5 -> PB0 -> (PWM, AIN0)  
1 -> 6 -> PB1 -> (PWM, AIN1)  
2 -> 7 -> PB2 -> (ADC1)  
3 -> 2 -> PB3 -> (ADC3)  
4 -> 3 -> PB4 -> (ADC2)  
5 -> 1 -> PB5 -> (RESET, ADC0)  

### Arduino code -> ATmega328 pin number -> Pin name -> Function

  -> 1 -> PC6 -> (RESET)  
0 -> 2 -> PD0 -> Digital pin 0 (Rx)  
1 -> 3 -> PD1 -> Digital pin 1 (Tx)  
2 -> 4 -> PD2 -> Digital pin 2  
3 -> 5 -> PD3 -> Digital pin 3 (PWM)  
4 -> 6 -> PD4 -> Digital pin 4  
5 -> 11 -> PD5 -> Digital pin 5  
6 -> 12 -> PD6 -> Digital pin 6  
7 -> 13 -> PD7 -> Digital pin 7  
8 -> 14 -> PB0 -> Digital pin 8  
9 -> 15 -> PB1 -> Digital pin 9 (PWM)  
10 -> 16 -> PB2 -> Digital pin 10 (PWM)  
11 -> 17 -> PB3 -> Digital pin 11 (PWM)  
12 -> 18 -> PB4 -> Digital pin 12  
13 -> 19 -> PB5 -> Digital pin 13  
14 -> 23 -> PC0 -> Analog input 0  
15 -> 24 -> PC1 -> Analog input 1  
16 -> 25 -> PC2 -> Analog input 2  
17 -> 26 -> PC3 -> Analog input 3  
18 -> 27 -> PC4 -> Analog input 4  
19 -> 28 -> PC5 -> Analog input 5  

## Atmega_Board_Programmer

### attiny85@16MHz internal

#### Before bootburning

>Signature = 0x1E 0x93 0x0B  
>Processor = ATtiny85  
>Flash memory size = 8192 bytes.  
>LFuse = 0x62  
>HFuse = 0xDF  
>EFuse = 0xFF  
>Lock byte = 0xFF  
>Clock calibration = 0x91  
>No bootloader support.  
>  
>First 256 bytes of program memory:  
>  
>00: 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF ...  

#### After bootburning

>Signature = 0x1E 0x93 0x0B  
>Processor = ATtiny85  
>Flash memory size = 8192 bytes.  
>LFuse = 0xF1  
>HFuse = 0xDF  
>EFuse = 0xFF  
>Lock byte = 0xFF  
>Clock calibration = 0x86  
>No bootloader support.  
>  
>First 256 bytes of program memory:  
>  
>00: 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF ...  

#### After programming

>Signature = 0x1E 0x93 0x0B  
>Processor = ATtiny85  
>Flash memory size = 8192 bytes.  
>LFuse = 0xF1  
>HFuse = 0xDF  
>EFuse = 0xFF  
>Lock byte = 0xFF  
>Clock calibration = 0x86  
>No bootloader support.  
>  
>First 256 bytes of program memory:  
>  
>00: 0x23 0xC0 0x32 0xC0 0x31 0xC0 0x30 0xC0 ...  

### ATmega328P as 'ATmega328/328P'  

#### After bootburning  

>Signature = 0x1E 0x95 0x0F  
>Processor = ATmega328P  
>Flash memory size = 32768 bytes.  
>LFuse = 0xFF  
>HFuse = 0xDF  
>EFuse = 0xFD  
>Lock byte = 0xCF  
>Clock calibration = 0xA5  
>Bootloader in use: No  
>EEPROM preserved through erase: No  
>Watchdog timer always on: No  
>Bootloader is 512 bytes starting at 7E00  
>  
>Bootloader:  
>  
>7E00: 0x11 0x24 0x84 0xB7 0x14 0xBE 0x81 0xFF ...  
>...  
>MD5 sum of bootloader = 0xFB 0xF4 0x9B 0x7B 0x59 0x73 0x7F 0x65 0xE8 0xD0 0xF8 0xA5 0x08 0x12 0xE7 0x9F  
>Bootloader name: optiboot_atmega328  
>  
>First 256 bytes of program memory:  
>  
>00: 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF ...  

### ATmega328P as 'Arduino Duemilanove or Diecemila'

#### After bootburning

>Signature = 0x1E 0x95 0x0F  
>Processor = ATmega328P  
>Flash memory size = 32768 bytes.  
>LFuse = 0xFF  
>HFuse = 0xDA  
>EFuse = 0xFD  
>Lock byte = 0xCF  
>Clock calibration = 0xA5  
>Bootloader in use: Yes  
>EEPROM preserved through erase: No  
>Watchdog timer always on: No  
>Bootloader is 2048 bytes starting at 7800  
>  
>Bootloader:  
>  
>7800: 0x0C 0x94 0x34 0x3C 0x0C 0x94 0x51 0x3C ...  
>...  
>MD5 sum of bootloader = 0x0A 0xAC 0xF7 0x16 0xF4 0x3C 0xA2 0xC9 0x27 0x7E 0x08 0xB9 0xD6 0x90 0xBC 0x02  
>Bootloader name: ATmegaBOOT_168_atmega328  
>  
>First 256 bytes of program memory:  
>  
>00: 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF 0xFF ...  

## Resources

[Breadboard @gammon.com](http://www.gammon.com.au/breadboard) (excellent!)  
[nickgammon arduino sketches @github](https://github.com/nickgammon/arduino_sketches)  
[Alternative Atmega bootloader programmer @gammon.com](http://www.gammon.com.au/forum/?id=11635)  
