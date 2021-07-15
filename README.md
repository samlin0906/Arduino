# RTC

//Wire Library

This library allows you to communicate with I2C / TWI devices. 
On the Arduino boards with the R3 layout (1.0 pinout), the SDA (data line) and SCL (clock line) are on the pin headers close to the AREF pin.

//DS3231 

is a serial RTC driven by a temperaturecompensated
32kHz crystal oscillator.

//Binary-Coded Decimal, BCD

There is no special standard for BCD numbers. There are no special data types for BCD code in Step7 either. 
BCD numbers are a subset of the hexadecimal numbers for which the data types BYTE, WORD and DWORD are used. 
Therefore, BCD numbers are entered as hexadecimal numbers in STEP7, but only the digits 0 to 9 are used, as in the decimal system. 
The hexadecimal digits A to F are not used. 
By using the BCD numbers on the basis of the 8421 code (is most frequently used and is also the best-known BCD coding), 
it is possible to represent numbers in a simplified manner. 
This makes it possible to represent binary words in such a way that the decimal value can be read digit by digit. 
https://www.sps-lehrgang.de/bcd-code/

//int DectoBCD(int Dec, unsigned char *Bcd, int length)
{
     int i;
     int temp;
 
     for(i=length-1; i>=0; i--)
     {
         temp = Dec%100;
         Bcd[i] = ((temp/10)<<4) + ((temp%10) & 0x0F);
         Dec /= 100;
     }
 
     return 0;

//unsigned long  BCDtoDec(const unsigned char *bcd, int length)
{
     int i, tmp;
     unsigned long dec = 0;
 
     for(i=0; i<length; i++)
     {
        tmp = ((bcd[i]>>4)&0x0F)*10 + (bcd[i]&0x0F);   
        dec += tmp * power(100, length-1-i);          
     }
 
     return dec;
}
http://www.cxyzjd.com/article/u010780613/50497058



