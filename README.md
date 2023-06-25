# IoT-Alarm-Clock
Smart IoT Alarm Clock
// include the library code:
#include <LiquidCrystal.h>
#include <Time.h>
#include <TimeLib.h>
// initialize the library by associating any needed LCD interface pin
// with the arduino pin number it is connected to const int rs = 1, en = 2, d4 = 4, d5 = 5, d6 = 6, d7 = 7; LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
void digitalClockDisplay()
{ lcd.print(hour()); printDigits(minute()); printDigits(second()); lcd.setCursor(0,1); lcd.print(" "); lcd.print(day()); lcd.print(" "); lcd.print(month()); lcd.print(" "); lcd.print(year());
if(hour() == 12 && minute() == 00 && second() == 10){ digitalWrite(8, HIGH); // Turn the LED on tone(9, 1000); // Send 1KHz sound signal...
delay(1000);        // ...for 1 sec noTone(9);     // Stop sound... delay(2000);        // ...for 1sec } }
void printDigits(int digits)
{ lcd.print(":"); if(digits < 10) lcd.print('0');
lcd.print(digits);
} void setup() {
//  struct tm* ptr; pinMode(9, OUTPUT); pinMode(8, OUTPUT);
//    time_t t;
//    t = time(NULL);
//    ptr = localtime(&t);
// set up the LCD's number of columns and rows:
lcd.begin(16, 2);
// Print a message to the LCD. //lcd.print(asctime(ptr)); setTime(12,00,0,14,05,22);
}
void loop()
// Turn off the display:
//  lcd.noDisplay();
//  delay(250); digitalClockDisplay(); // Turn on the display:
lcd.display(); delay(250); lcd.clear();
}
