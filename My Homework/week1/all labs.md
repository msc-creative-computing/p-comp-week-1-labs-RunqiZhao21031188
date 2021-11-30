# lab1

## project 1

<img src="https://github.com/RunqiZhao21031188/1/blob/main/W1L1p1.jpeg" width="300px" height="300px" alt="lab00-01"/>

<img src="https://github.com/RunqiZhao21031188/1/blob/main/W1L1p1.3.jpeg" height="300px" alt="lab00-01"/>

this is my video link
https://github.com/RunqiZhao21031188/1/blob/main/W1L1P1.mp4
<img src="https://github.com/RunqiZhao21031188/1/blob/main/W1L1P1.mp4" width="300px" height="300px" alt="lab00-01"/>


## project 2

<img src="https://github.com/RunqiZhao21031188/1/blob/main/W1L1p2.jpeg" width="300px" height="300px" alt="lab00-01"/>
<img src="https://github.com/RunqiZhao21031188/1/blob/main/W1L1p2.2.jpeg" width="300px" height="300px" alt="lab00-01"/>
this is my video link
https://github.com/RunqiZhao21031188/1/blob/main/W1L1p2.mp4
<img src="https://github.com/RunqiZhao21031188/1/blob/main/W1L1p2.mp4" width="300px" height="300px" alt="lab00-01"/>

### coding
int switchState = 0;

void setup() {
  // put your setup code here, to run once:
 pinMode(3,OUTPUT);
 pinMode(4,OUTPUT);
 pinMode(5,OUTPUT);
 pinMode(2,INPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  switchState = digitalRead(2);
  
  if (switchState == LOW) { 
 // the buton is not pressed
  digitalWrite(3, HIGH); // green LED
  digitalWrite(4, LOW); // red LED
  digitalWrite(5, LOW); // red LED
 }
 else { // the buton is pressed
 digitalWrite(3, LOW); 
 digitalWrite(4, LOW);
 digitalWrite(5, HIGH);
 delay(250); // wait for a quarter second
 // toggle the LEDs
 digitalWrite(4, HIGH); 
 digitalWrite(5, LOW);
 delay(250); // wait for a quarter second
 } 
}

## project 3

<img src="https://github.com/RunqiZhao21031188/1/blob/main/W1L1p3.1.png" width="300px" height="300px" alt="lab00-01"/>
<img src="https://github.com/RunqiZhao21031188/1/blob/main/W1L1p2.2.jpeg" width="300px" height="300px" alt="lab00-01"/>

### coding

const int sensorPin=A0;
const float baselineTemp = 20.0;


void setup(){
Serial.begin(9600);
for(int pinNumber = 2; pinNumber<5; pinNumber++){
pinMode(pinNumber,OUTPUT);
digitalWrite(pinNumber, LOW);
 } 
}
void loop(){
int sensorVal = analogRead(sensorPin);

Serial.print("Sensor Value: "); 
Serial.print(sensorVal);

 // convert the ADC reading to voltage
float voltage = (sensorVal/1024.0) * 5.0;

Serial.print(", Volts:");
Serial.print(voltage);

Serial.print(", degrees C:");

 // convert the voltage to temperature in degrees
float temperature = (voltage - .5) * 100;
Serial.println(temperature);

if(temperature < baselineTemp){
digitalWrite(2, LOW);
digitalWrite(3, LOW);
digitalWrite(4, LOW);

}else if(temperature >= baselineTemp+2 && 
 temperature < baselineTemp+4){
digitalWrite(2, HIGH);
digitalWrite(3, LOW);
digitalWrite(4, LOW);

}else if(temperature >= baselineTemp+4 && 
 temperature < baselineTemp+6){
digitalWrite(2, HIGH);
digitalWrite(3, HIGH);
digitalWrite(4, LOW);

 }else if(temperature >= baselineTemp+6){
digitalWrite(2, HIGH);
digitalWrite(3, HIGH);
digitalWrite(4, HIGH);

 }
delay(1);
}
# lab2
This is my Tinkercad link
https://www.tinkercad.com/things/7oPvmV7zv1R-frantic-bombul-fyyran/editel?sharecode=bMdHo7DMjMO2QcpXRSo4g2IF2GBg5O6QFsZuSLf7Jvk
<img src="https://github.com/RunqiZhao21031188/1/blob/main/931634727743_.pic_hd.jpg" width="300px" height="300px" alt="lab00-01"/>
<img src="https://github.com/RunqiZhao21031188/1/blob/main/931634727743_.pic_hd.jpg" width="300px" height="300px" alt="lab00-01"/>

this is my video link
https://github.com/RunqiZhao21031188/1/blob/main/W1L1p2.mp4
<img src="https://github.com/RunqiZhao21031188/1/blob/main/W1L1p2.mp4" width="300px" height="300px" alt="lab00-01"/>

coding
// C++ code
//
int led=8;
int t=9;
int e=10;
int gnd=11;
int voice=12;
  
float cm;
float temp;

void setup()
{
  Serial.begin(9600);
  pinMode(t,OUTPUT);
  pinMode(e,INPUT);
  pinMode(led,OUTPUT);
  pinMode(voice,OUTPUT);
  
}

void loop()
{
  digitalWrite(t, LOW);
  delay(20); // Wait for 1000 millisecond(s)
  digitalWrite(t, HIGH);
  delay(20); // Wait for 1000 millisecond(s)
  digitalWrite(t, LOW);
  
 
  temp = float(pulseIn(e,HIGH));
  
  cm = (temp * 17 )/1000;  //(temp * (34000/1000000))/2
  Serial.print("Echo =");
  Serial.print(temp);
  Serial.print(" | | Distance = ");
  Serial.print(cm);
  Serial.println("cm");
  if (cm < 200)
  {
     digitalWrite(led,HIGH);
     digitalWrite(voice,HIGH);
  }
  else{
     digitalWrite(led,LOW);
     digitalWrite(voice,LOW);
  }
  delay(100);
  
}
