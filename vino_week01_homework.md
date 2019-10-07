# week01_homework
#honework
The program is base on the rule of ‘simonsays’.
The green LED represents ’simonsays’.
And the red & orange LED represent two actions.
Here is the coding part.
press two switch in the same time to start the game.
If game over, the green LED will keep flashing.
And if the game start, the LED(pin13) will turn on.
Only when the green LED and arbitrarily light on then be allowed to press the switch.
If the green LED didn’t on but any switch be turned on, then lost.(keep waiting for just a second to skip the green LED)
All the LED will be turn on randomly during the game is running.
Below is the coding part.
And here is the video link:[vino_week01_homework on Vimeo](https://vimeo.com/364530183)
- - - -

``` c
#include <time.h>

const int redled = 3;
const int orgled = 5;
const int greled = 2;
const int buttonorg = 6;
const int buttonred = 4;
int gameover = 1;
int simonsays = 1;
int whichlighton = 0;
void setup() {
  pinMode(4,OUTPUT);
  pinMode(3,OUTPUT);
  pinMode(2,OUTPUT);
  pinMode(5,INPUT);
  pinMode(6,INPUT); 
  pinMode(13,OUTPUT); 

}
void loop() {
  if(gameover == 1){
    whichlighton = rand()%2;
    simonsays = rand()%2;
    digitalWrite(redled,LOW);
    digitalWrite(orgled,LOW);
    digitalWrite(13,LOW); 
    digitalWrite(greled,HIGH); 
    delay(500);
    digitalWrite(greled,LOW);
    delay(500); 
    } 
    
     if(digitalRead(buttonred) && digitalRead(buttonorg))
  {
    digitalWrite(13,HIGH);  
    gameover = 0;
    }


  if(gameover == 0){
    
   if(simonsays == 1){
    digitalWrite(whichlighton*2+3,HIGH);
    digitalWrite(greled,HIGH);
    if(digitalRead(whichlighton*2+3+1) == HIGH){
      digitalWrite(whichlighton*2+3,LOW);
      digitalWrite(greled,LOW);
      whichlighton = rand()%2;
      simonsays = rand()%2;
      delay(2000);
      }
    if(whichlighton == 0 && digitalRead(6))
    {gameover = 1;}
    if(whichlighton == 1 && digitalRead(4))
    {gameover = 1;}
   }
   if(simonsays == 0){
    digitalWrite(whichlighton*2+3,HIGH);
    digitalWrite(greled,LOW);
    delay(500);
    digitalWrite(redled,LOW);
    digitalWrite(orgled,LOW);
    whichlighton = rand()%2;
    simonsays = rand()%2;  
    if(digitalRead(buttonred)||digitalRead(buttonorg)){gameover = 1;} 
    }
    
    }
}
```
