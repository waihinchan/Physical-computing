# week01 homework
#honework
The program is base on the rule of ‘simonsays’.<br>
The green LED represents ’simonsays’.<br>
And the red & orange LED represent two actions.<br>
Here is the coding part.<br>
press two switch in the same time to start the game.<br>
If game over, the green LED will keep flashing.<br>
And if the game start, the LED(pin13) will turn on.<br>
Only when the green LED and arbitrarily light on then be allowed to press the switch.<br>
If the green LED didn’t on but any switch be turned on, then lost.(keep waiting for just a second to skip the green LED)<br>
All the LED will be turn on randomly during the game is running.<br>
Below is the coding part.<br>
And here is the video link:[vino_week01_homework on Vimeo](https://vimeo.com/364530183)<br>
- - - -
#include <time.h>
//时间头文件
const int redled = 3;
const int orgled = 5;
const int greled = 2;
const int buttonorg = 6;
const int buttonred = 4;
//定义各个零件的pin口//
//const转换成常亮不可更改
int gameover = 1;
int simonsays = 1;
int whichlighton = 0;//参数：随机控制哪一个灯是亮//
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
    } //gameover状态下led灯关闭，绿色灯不断闪烁
    
     if(digitalRead(buttonred) && digitalRead(buttonorg))
  {
    digitalWrite(13,HIGH);  
    gameover = 0;
    }
  //如果两个按钮同时按下，则游戏开始，此时ganmeover状态变为0//

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
