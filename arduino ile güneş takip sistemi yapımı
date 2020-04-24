#include <Servo.h> //Servo kütüphanesi
 
// 180 horizontal MAX
Servo horizontal;
int servoh = 180;
 
int servohLimitHigh = 180;
int servohLimitLow = 65;
Servo vertical;
int servov = 45;
 
int servovLimitHigh = 80;
int servovLimitLow = 15;
// LDR pin connections
// name = analogpin;
int ldrlt = 0; //LDR sol üst
int ldrrt = 1; //LDR sağ üst
int ldrld = 2; //LDR sol alt
int ldrrd = 3; //LDR sağ alt
 
void setup()
{
Serial.begin(9600);
// servo connections
// name.attacht(pin);
horizontal.attach(9);
vertical.attach(10);
horizontal.write(180);
vertical.write(45);
delay(3000);
}
 
void loop()
{
int lt = analogRead(ldrlt); // sol üst
int rt = analogRead(ldrrt); // sağ üst
int ld = analogRead(ldrld); // sol alt
int rd = analogRead(ldrrd); // sağ alt
 
// int dtime = analogRead(4)/20;
// int tol = analogRead(5)/4;
int dtime = 10;
int tol = 50;
 
int avt = (lt + rt) / 2; // average value top
int avd = (ld + rd) / 2; // average value down
int avl = (lt + ld) / 2; // average value left
int avr = (rt + rd) / 2; // average value right
 
int dvert = avt - avd; // check the diffirence of up and down
int dhoriz = avl - avr;// check the diffirence og left and rigt
 
 
Serial.print(avt);
Serial.print(" ");
Serial.print(avd);
Serial.print(" ");
Serial.print(avl);
Serial.print(" ");
Serial.print(avr);
Serial.print(" ");
Serial.print(dtime);
Serial.print(" ");
Serial.print(tol);
Serial.println(" ");
 
 
if (-1*tol > dvert || dvert > tol)
{
if (avt > avd)
{
servov = ++servov;
if (servov > servovLimitHigh)
{
servov = servovLimitHigh;
}
}
else if (avt < avd)
{
servov= --servov;
if (servov < servovLimitLow) { servov = servovLimitLow; } } vertical.write(servov); } if (-1*tol > dhoriz || dhoriz > tol)
{
if (avl > avr)
{
servoh = --servoh;
if (servoh < servohLimitLow)
{
servoh = servohLimitLow;
}
}
else if (avl < avr) { servoh = ++servoh; if (servoh > servohLimitHigh)
{
servoh = servohLimitHigh;
}
}
else if (avl = avr)
{
// nothing
}
horizontal.write(servoh);
}
delay(dtime);
 
}
