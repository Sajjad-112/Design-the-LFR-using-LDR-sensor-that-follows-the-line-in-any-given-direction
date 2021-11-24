# Design-the-LFR-using-LDR-sensor-that-follows-the-line-in-any-given-direction
int left_wheelA = 14; int left_wheelB = 12;
int right_wheelA = 26; int right_wheelB = 27;
int left_wheel_EN = 33; int right_wheel_EN = 32;
const int Analog_channel_pin= 36;
int ADC_VALUE = 0;
int voltage_value = 0;
void setup()
{
pinMode(left_wheelA, OUTPUT); pinMode(left_wheelB, OUTPUT);
pinMode(right_wheelA, OUTPUT); pinMode(right_wheelB, OUTPUT);pinMode(left_wheel_EN, OUTPUT);
pinMode(right_wheel_EN, OUTPUT);
Serial.begin(9600);
}
void loop()
{
ADC_VALUE = analogRead(Analog_channel_pin);
Serial.print("ADC VALUE = ");
Serial.println(ADC_VALUE);
Serial.println("");
delay(1000);
voltage_value = (ADC_VALUE * 3.3 ) / (4095);
Serial.print("Voltage = ");
Serial.print(voltage_value);
Serial.print("volts");
Serial.println("");
delay(1000);
if(voltage_value < 8)
{
digitalWrite(left_wheelA, LOW); digitalWrite(left_wheelB, HIGH);
digitalWrite(right_wheelA, LOW); digitalWrite(right_wheelB, HIGH);
}
else
{
turn_left();
}
}
void turn_left(void)
{
digitalWrite(left_wheelA, LOW); digitalWrite(left_wheelB, HIGH);
digitalWrite(right_wheelA, HIGH); digitalWrite(right_wheelB, LOW);
}
