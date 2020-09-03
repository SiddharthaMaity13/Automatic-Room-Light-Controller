# Automatic-Room-Light-Controller
Aiming the working process of Arduino uno and PIR sensor, the project first deals with the sensitivity detector of people inside a room using PIR sensor, then the paper optimizes the state of Arduino Uno board . its future developments and applications in different fields. power consumption can be optimized and store it for further usage.Our society will get various benefits in the fulfilment of this project.  

Code:
#include<LiquidCrystal.h>
LiquidCrystal lcd(13,12,11,10,9,8);
#define in 14
#define out 19
#define relay 2
int count=0;
void IN()
{
    count++;
    lcd.clear();
    lcd.print("Person In Room:");
    lcd.setCursor(0,1);
    lcd.print(count);
    delay(1000);
}
void OUT()
{
  count--;
    lcd.clear();
    lcd.print("Person In Room:");
    lcd.setCursor(0,1);
    lcd.print(count);
    delay(1000);
}
void setup()
{
  lcd.begin(16,2);
  lcd.print("Visitor Counter");
  delay(2000);
  pinMode(in, INPUT);
  pinMode(out, INPUT);
  pinMode(relay, OUTPUT);
  lcd.clear();
  lcd.print("Person In Room:");
  lcd.setCursor(0,1);
  lcd.print(count);
}
void loop()
{  
  
  if(digitalRead(in))
  IN();
  if(digitalRead(out))
  OUT();
  
  if(count<=0)
  {
    lcd.clear();
    digitalWrite(relay, LOW);
    lcd.clear();
    lcd.print("Nobody In Room");
    lcd.setCursor(0,1);
    lcd.print("Light Is Off");
    delay(200);
  }
  
  else
    digitalWrite(relay, HIGH);
  
}

