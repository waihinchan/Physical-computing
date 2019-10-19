# vino_week02_homework
#作业

## LB00 **Leds in Serial and Parallel**
### Experiment procedure
![](vino_week02_homework/IMG_3421.jpeg)
### Result:
1. The serial circuit can connect no more than 2 LED(according to the different resistor value the result may have different situation.)
2. The parallel  circuit can connect over 6 and more LED.(Actually I think the amount would more than 6, depend on the power of the LEDS)
### Reason:
As we know that the current are the same in the serial circuit, according to I = V/R,  so each LED divide the total voltage. So the more LED be connected in the circuit, the less voltage each LED get. When the voltage is too low, then unable to support the design power of the LED.

As for the parallel circuit, each path share the same voltage. Also in the parallel circuit, the resistor value less than either one of them(LED).
And the amount of how much LED can be connected in the circuit depends on the power of the VCC, as long as it doesn’t over the VI.(also many factor would effect the result such as the heat issue.)
- - - -
## LB01 **Serial Data**
``` arduino
void setup() {
  // put your setup code here, to run once:
Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:
  delay(3000);
  Serial.println(“The Old Man and the Old Cat”);
  delay(3000);
  Serial.print(“An old man has a cat.”);
  delay(3000);
  Serial.print(“The cat is very old, too.”);
  delay(3000);
  Serial.println(“He runs very quickly.”);
  delay(3000);
  Serial.print(“And his teeth are bad.”);
  delay(3000);
  Serial.println(“One evening, the old cat sees a little mouse.”);
  delay(3000);
  Serial.println(“ He catches it, but he can’t eat it because his teeth are not strong enough.”);
  delay(3000);
  Serial.println(“The mouse runs away.”);
  delay(3000);

}
```

![](vino_week02_homework/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202019-10-19%20%E4%B8%8B%E5%8D%883.06.42.png)
### Expansion
The difference between "serial.print" and "serial.write"
``` arduino
int I = 97 ;
void setup() 
{ 
 Serial.begin( 9600 );
Serial.print( I );
delay( 10 );
Serial.write( I );
}
void loop()
{
}
```
The result would be “97a”
Another sample:
``` arduino
int  I =  0x7A ;
void setup() 
{ 
 Serial.begin( 9600 );
Serial.print( I  );
delay(10);
Serial.write( I );
}
void loop()
{
}
```
The result would be “31 32 32 7A”.
The different is the “print" sending the character, while the "write"  sending the byte.
- - - -
## LB02 **Potentiometers (Knobs)**
Base on [Arduino - Potentiometer](https://www.arduino.cc/en/tutorial/potentiometer)
Video link: [Potentiometers (Knobs) on Vimeo](https://vimeo.com/367450355)
![](vino_week02_homework/6C7A6A74-2BC8-458E-AAFB-498EDE93193C.png)
- - - -
## LB03 **Light Dependent Resistors**

![](vino_week02_homework/1430caf8-3eed-4c89-a186-e20e0a93575b.JPG)
- - - -
## LB04 **Playing with Common Sensors**

![](vino_week02_homework/6be48273-ee81-4730-a2aa-2d7d18f32004.JPG)