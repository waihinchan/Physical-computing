# week01 homework
#honework
The program is base on the rule of ‘simonsays’.<br>
The green LED represents ’simonsays’.<br>
And the red & orange LED represent two actions.<br>
Unfortunately I found that the bread board had no more extra space to capacity 3 switch and more LEDS.(I think maybe I can use the other side of the bread board but the wires will tangle together.)<br>
Here is the coding part.<br>
press two switch in the same time to start the game.<br>
If game over, the green LED will keep flashing.<br>
And if the game start, the LED(pin13) will turn on.<br>
Only when the green LED and arbitrarily light on then be allowed to press the switch.<br>
If the green LED didn’t on but any switch be turned on, then lost.(keep waiting for just a second to skip the green LED)<br>
All the LED will be turn on randomly during the game is running.<br>
Below is the coding part.<br>
And here is the video link:[vino_week01_homework on Vimeo](https://vimeo.com/364530183)<br>
< font color=red>color
- - - -
``` c
int switchState1=0;
int switchState2=0;

void setup() {
pinMode(6,OUTPUT);
pinMode(4,OUTPUT);
pinMode(5,OUTPUT);
pinMode(2,INPUT);
pinMode(8,INPUT);

}

void loop() {
switchState2=digitalRead(2);
switchState1=digitalRead(8);

if(switchState1==LOW)

switch (switchState2){
 case LOW:  {
  digitalWrite(4,HIGH); 
digitalWrite(5,LOW);
digitalWrite(6,LOW);
delay(500);
digitalWrite(4,LOW); 
digitalWrite(5,HIGH);
delay(500);
digitalWrite(5,LOW);
digitalWrite(6,HIGH);
delay(500);
}

 case HIGH:{
  digitalWrite(4,LOW);
delay(250);
digitalWrite(4,HIGH);
delay(50);
 }
} 

 
else if (switchState1==HIGH){
  
switch (switchState2){
 case LOW:  {
  digitalWrite(4,LOW);
delay(500);
digitalWrite(4,HIGH);
delay(500);
digitalWrite(5,LOW);
delay(500);
digitalWrite(5,HIGH);
delay(500);
digitalWrite(6,LOW);
delay(500);
digitalWrite(6,HIGH);
delay(500);

}

 
case HIGH : {
 digitalWrite(4,HIGH);
digitalWrite(5,HIGH);
digitalWrite(6,HIGH);
delay(200);

digitalWrite(4,LOW);
delay(50);
digitalWrite(5,LOW); 
delay(25);
digitalWrite(6,LOW);
delay(15);

}

return 0;
}

 }
 
}
```
