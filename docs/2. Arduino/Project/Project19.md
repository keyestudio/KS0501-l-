### Project 19 8*16 dot matrix-light control

**1.Project Instruction**

The light sensor feature that resistance is inverse proportion to to light intensity. Based on this characteristics, we made a night light. In this chapter, we will show you light column on dot matrix.

**2.Project Principle**

The signal pin of light sensor is linked with A6 of MAX development board. 8*16 dot matrix will show light column, the darker the light intensity is, the shorter the height of light column.

**3.Project circuit**

![](media/57.png)

**4.Project code**

```c
/*
keyestudio Max Development Board
Project 19
8*16 dot matrix-light control
http://www.keyestudio.com
*/
#include <Wire.h>
#include "Keyestudio_LEDBackpack.h"
#include "Keyestudio_GFX.h"
int light = A6;
int Light_val;
Keyestudio_8x16matrix matrix = Keyestudio_8x16matrix();

void setup() 
{
  Serial.begin(9600);
  Serial.println("16x8 LED Matrix Test");
  pinMode(A6,INPUT);
  matrix.begin(0x70);  // pass in the address
}

void loop() 
{
  Light_val=analogRead(A6);
  Light_val=map(Light_val,0,1023,0,15);
   matrix.clear();
  matrix.drawLine(3,0, 3,Light_val, LED_ON);
  matrix.writeDisplay();  // write the changes we just made to the display
  delay(10);
}
```

**5.Project results**

Wire up, open Arduino IDE and download code. Place the control board as follows:

![](media/58.png)

The photoresistor of control board detects the light intensity. The stronger the light intensity is, the more LED on.