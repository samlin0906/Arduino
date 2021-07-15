# Arduino
# 12C
# RTC

Wire Library
This library allows you to communicate with I2C / TWI devices. 
On the Arduino boards with the R3 layout (1.0 pinout), the SDA (data line) and SCL (clock line) are on the pin headers close to the AREF pin.

The DS3231 is a serial RTC driven by a temperaturecompensated
32kHz crystal oscillator.

Binary-Coded Decimal, BCD
BCD 數字是使用BYTE、WORD 和 DWORD 數據類型的十六進制數字的子集。因此，BCD 數字在 STEP7 中輸入為十六進制數字，
但僅使用數字 0 到 9，如在十進制系統中。不使用十六進制數字 A 到 F。通過在 8421 編碼（最常用）的基礎上使用 BCD 數字，
可以以簡化的方式表示數字。這使得以可以逐位讀取十進制值的方式來表示二進製字成為可能。
https://www.sps-lehrgang.de/bcd-code/

int DectoBCD(int Dec, unsigned char *Bcd, int length)
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

unsigned long  BCDtoDec(const unsigned char *bcd, int length)
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



