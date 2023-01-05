// Reads water & co quality from two sensors and displays in the lcd display
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

// Set the LCD address to 0x27 for a 16 chars and 2 line display
LiquidCrystal_I2C lcd(0x27, 16, 2);

#define POWER_PIN1 7
#define SIGNAL_PIN1 A2
#define POWER_PIN2 8
#define SIGNAL_PIN2 A3
#define CO_PIN1 A0
#define CO_PIN2 A1

int water_quality1 = 0;  // variable to store the sensor value
int water_quality2 = 0;  // varia ble to store the sensor value
int co_value1 = 0;
int co_value2 = 0;

void setup() {
  // initialize the LCD
  lcd.begin();

  // Turn on the blacklight and print a message.
  lcd.backlight();
  Serial.begin(9600);
  pinMode(POWER_PIN1, OUTPUT);    // configure D7 pin as an OUTPUT
  digitalWrite(POWER_PIN1, LOW);  // turn the sensor OFF
  pinMode(POWER_PIN2, OUTPUT);    // configure D7 pin as an OUTPUT
  digitalWrite(POWER_PIN2, LOW);  // turn the sensor OFF
}

void loop() {
  digitalWrite(POWER_PIN1, HIGH);   // turn the sensor ON
  delay(10);                       // wait 10 milliseconds
  water_quality1 = analogRead(SIGNAL_PIN1);  // read the analog value from sensor
  digitalWrite(POWER_PIN1, LOW);    // turn the sensor OFF
  
  digitalWrite(POWER_PIN2, HIGH);   // turn the sensor ON
  delay(10);                       // wait 10 milliseconds
  water_quality2 = analogRead(SIGNAL_PIN2);  // read the analog value from sensor
  digitalWrite(POWER_PIN2, LOW);    // turn the sensor OFF

  co_value1 = analogRead(CO_PIN1);
  co_value2 = analogRead(CO_PIN2);

  lcd.clear();
  lcd.print("CO quality 1: ");
  lcd.setCursor(0, 1);
  lcd.print(co_value1, DEC);
  delay(3000);

  lcd.clear();
  lcd.print("CO quality 2: ");
  lcd.setCursor(0, 1);
  lcd.print(co_value2, DEC);
  delay(3000);

  lcd.clear();
  lcd.print("Water quality 1: ");
  lcd.setCursor(0, 1);
  lcd.print(water_quality1, DEC);
  delay(3000);

  lcd.clear();
  lcd.print("Water quality 2: ");
  lcd.setCursor(0, 1);
  lcd.print(water_quality2, DEC);
  delay(3000);
}
