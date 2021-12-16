
# final project--Be Nice

youtube link
https://youtu.be/9WfamLFYHkw

## inspiration
I saw a news story on TV a few weeks ago about guide dogs and the training they receive. 
They need to resist the temptation of food and playing with other dogs. They are retired in 
advance and their average life expectancy is reduced because of their difficult lifestyle. This 
brings me to the topic of animal exploitation and deprivation.
Our common service animals like horses and dogs. Horses are more involved with training, 
such as horse racing and jumping. I myself really like horseback riding, but in the process of 
training, I really can't determine whether the horse loves or hates the sport. These things will 
be a part of their lives due to day to day training, and they may lose their nature and may 
not know if they like this activity.

### I'm not trying to criticize the practice of taining animals, just thinking the relationship between people and service animals.

## the problems in training process
People may beat animals to conquer them with violence.
Try to scare the animals.
Treat animals as tools.

## concept
It simulates the process of human training animals and makes people think about the relationship with service animals.
Mimicking the feelings of animals and transmitting them more directly to humans.

## idea
### sound
The volume of a person's voice can get a feedback of the animal's mood(LED change color).
### distance
Different distences have different interactions.

## THE TERA
Tera is a new concept of a service animatronic. It's not as submissive as a real animal.To train it, you have to be patient and friendly. You need to think and explore how to better interact with it. If you do it correctly, it responds to you.

## tools
### input
ultrasonic distance sensor
sound sensor
###
Servo x2
RGB LED x2

## interaction

<img src="https://github.com/RunqiZhao21031188/1/blob/main/%E6%88%AA%E5%B1%8F2021-12-01%20%E4%B8%8B%E5%8D%889.06.20.png" width="300px" height="300px" alt="lab00-01"/>




## coding
```javascript
// C++ code
//
#include <Servo.h>


const int redPin=7;
const int bluePin=6;
const int greenPin=5;
const int soundPin=A0;
int threshold=0;

int Dt=9;
int De=10;
int gnd=11;
int pos = 0;
int mid =0;
Servo servo_12;
Servo servo_2;

int speaker =13;



int timeReleased = 0;


  
float cm;
float temp;

void setup()
{
  Serial.begin(9600);
  pinMode(Dt,OUTPUT);
  pinMode(De,INPUT);
  

  
  pinMode(redPin,OUTPUT);
  pinMode(bluePin,OUTPUT);
  pinMode(greenPin,OUTPUT);
  pinMode(soundPin,INPUT);

  pinMode(speaker,OUTPUT);



 analogWrite(redPin,255);
 analogWrite(bluePin,255);
 analogWrite(greenPin,255);

 
 
  servo_12.attach(12);
  servo_2.attach(3);

 
  
}

void loop()
{
  digitalWrite(Dt, LOW); //超声波
  delay(20); // Wait for 1000 millisecond(s)
  digitalWrite(Dt, HIGH);
  delay(20); // Wait for 1000 millisecond(s)
  digitalWrite(Dt, LOW);
  
 
  temp = float(pulseIn(De,HIGH));
  
  cm = (temp * 17 )/1000;  //(temp * (34000/1000000))/2
  Serial.print("Echo =");
  Serial.print(temp);
  Serial.print(" | | Distance = ");
  Serial.print(cm);
  Serial.println("cm");
  
  if (cm < 200)
  {
      analogWrite(redPin,0);
      analogWrite(bluePin,0);
      analogWrite(greenPin,0);
     for (pos = 0; pos <= 90; pos += 1) {
    // tell servo to go to position in variable 'pos'
     servo_12.write(pos);
    // wait 15 ms for servo to reach the position
    
    }
    
     
  
  }
  else{
     
      for (pos = 90; pos >= 0; pos -= 1) {
    // tell servo to go to position in variable 'pos'
    servo_12.write(pos);
    // wait 15 ms for servo to reach the position
    
   }
    threshold = analogRead(soundPin);
  
        Serial.println(threshold);
        delay(100);
        Serial.println(mid);
        delay(1000);
  
        if ((65>threshold)&&(threshold>=20)){
           analogWrite(redPin,0); //green light
           analogWrite(bluePin,255);
           analogWrite(greenPin,255);
           delay(500);
           tone(13, 900, 500); // play tone 69 (A5 = 880 Hz)
           delay(500); // Wait for 200 millisecond(s)
  // turn off tone function for pin 6:
           noTone(13);
  // play a note on pin 7 for 500 ms:
  
           delay(100); // Wait for 500 millisecond(s)
           mid +=1;
           if(mid>=2){
            for (pos = 90; pos >= 0; pos -= 1) {
    // tell servo to go to position in variable 'pos'
           servo_2.write(pos);
    // wait 15 ms for servo to reach the position
    
   }
           }
 
         }
     
        else if (threshold>=65){ 
           analogWrite(redPin,255);//red light
           analogWrite(bluePin,0);
           analogWrite(greenPin,0);
           delay(1000);
           tone(13, 15, 1500); // play tone 69 (A5 = 880 Hz)
           delay(1000); // Wait for 200 mi/llisecond(s)
  // turn off tone function for pin 6:
           noTone(13);
  // play a note on pin 7 for 500 ms:
  
           delay(100); // Wait for 500 millisecond(s)
           mid=0;
 
         }
        else{
           analogWrite(redPin,255);
           analogWrite(bluePin,255);
           analogWrite(greenPin,255);
           delay(500);
           mid=0;
         }
       }
  delay(100);
  
}
 ```


## tinkercad 
Tinkercad does not have a Sound sensorr. I use it instead to show the circuit connections
（Sound Sensor is used for code and circuit）

Tinkercad link https://www.tinkercad.com/things/8UA4x7RwrSi-final-project-by-runqi-zhao/editel?sharecode=8JYXAnfU0olPO5CdUxpaR6HMVhJTPwG3OTCacZnDfek

<img src="https://github.com/RunqiZhao21031188/1/blob/main/%E6%88%AA%E5%B1%8F2021-12-01%20%E4%B8%8B%E5%8D%884.47.13.png" width="300px" height="300px" alt="lab00-01"/>


## prototype 
<img src="https://github.com/RunqiZhao21031188/1/blob/main/%E6%88%AA%E5%B1%8F2021-12-01%20%E4%B8%8B%E5%8D%889.14.41.png" width="300px" height="300px" alt="lab00-01"/>
<img src="https://github.com/RunqiZhao21031188/1/blob/main/%E6%88%AA%E5%B1%8F2021-12-01%20%E4%B8%8B%E5%8D%889.14.50.png" width="300px" height="300px" alt="lab00-01"/>
<img src="https://github.com/RunqiZhao21031188/1/blob/main/%E6%88%AA%E5%B1%8F2021-12-01%20%E4%B8%8B%E5%8D%889.15.12.png" width="300px" height="300px" alt="lab00-01"/>
<img src="https://github.com/RunqiZhao21031188/1/blob/main/%E6%88%AA%E5%B1%8F2021-12-01%20%E4%B8%8B%E5%8D%889.16.09.png" width="300px" height="300px" alt="lab00-01"/>


