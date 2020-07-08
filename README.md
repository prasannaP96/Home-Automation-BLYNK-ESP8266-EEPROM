# Prasanna-kumar
#define BLYNK_PRINT Serial
#include <EEPROM.h>
#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266_SSL.h>

// You should get Auth Token in the Blynk App.
// Go to the Project Settings (nut icon).
char auth[] = "your Auth code";

// Your WiFi credentials.
// Set password to "" for open networks.
char ssid[] = "WIFI name ";
char pass[] = "WIFI password";
bool flag1;
bool flag2;
bool flag3;
bool flag4;
void recall();
void setup()
{
    digitalWrite(16, HIGH);
    digitalWrite(5, HIGH);
    digitalWrite(4, HIGH);
    digitalWrite(0, HIGH);
    digitalWrite(2, HIGH);
    pinMode(16, OUTPUT);
    pinMode(5,OUTPUT);
    pinMode(4, OUTPUT);
    pinMode(0,OUTPUT);
    EEPROM.begin(512);
    Serial.begin(9600);
    recall();
  Blynk.begin(auth, ssid, pass);
}

void loop()
{
 
  if ( digitalRead(16)==HIGH)
 {
  digitalWrite(16, HIGH);  
  EEPROM.write(1,true);
  EEPROM.commit();
 }
 else if(digitalRead(16)==  LOW)
 {
  EEPROM.write(1,false);
  EEPROM.commit();
 }
  if ( digitalRead(5)==HIGH)
 {
  digitalWrite(5, HIGH);  
  EEPROM.write(2,true);
  EEPROM.commit();
 }
 else if(digitalRead(5)==  LOW)
 {
  EEPROM.write(2,false);
  EEPROM.commit();
 }
 if ( digitalRead(4)==HIGH)
 {
  digitalWrite(4, HIGH);  
  EEPROM.write(3,true);
  EEPROM.commit();
 }
 else if(digitalRead(4)==  LOW)
 {
  EEPROM.write(3,false);
  EEPROM.commit();
 }
  if ( digitalRead(0)==HIGH)
 {
  digitalWrite(0, HIGH);  
  EEPROM.write(4,true);
  EEPROM.commit();
 }
 else if(digitalRead(0)==  LOW)
 {
  EEPROM.write(4,false);
  EEPROM.commit();
 }
 
  Blynk.run();
}
void recall()
{
  flag1 = EEPROM.read(1);
  flag2 = EEPROM.read(2);
  flag3 = EEPROM.read(3);
  flag4 = EEPROM.read(4);
  
  digitalWrite(16,flag1);
  digitalWrite(5,flag2);
  digitalWrite(4,flag3);
  digitalWrite(0,flag4);
  
}
  
