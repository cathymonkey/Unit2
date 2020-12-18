# Unit 2
## Project 1: 7-segment Number display
### Criteria A: Planning
#### Context of the problem 
Inspired from classical 7-segment Number display(fig.1), we are going to make our own number display. The number display will include 7 LEDs maximum and 4 buttons maximum.

<img src ="https://github.com/cathymonkey/Unit2/blob/main/7display.jpeg" width = "250" height = "250">

*fig1. Classical 7-segment number display* 

#### Justification of the solution
We want to create a display using 7 LEDs，4 buttons and arduino Uno R3. It will look like a Christmas tree. There will be four rows and each row will be represented as a digit. Each row will be controlled independently by each button. When all the LEDs in a row are on, the digit it represents is 1 in binary; oppositely, when all the LEDs in a row are off, the digit is 0. If none of the LEDs are on, which means the buttons are not pressed, it is 0 in base 10. 

Here is a visual explanation. 

![fig1](https://github.com/cathymonkey/Unit2/blob/main/fig1.jpeg)

*fig2. Sketch for our own number display*

#### Success Criteria
1. The display should count from 0-9.
2. The format of the number 0-9 is included.
3. Information indicating what the buttons do is included.
4. The display uses maximum 7 LEDs and 4 buttons.

### Criteria B: Design 
<img src = "https://lh3.googleusercontent.com/-CRtVAWyfHKc/X6vuUtirlKI/AAAAAAAAAW4/lNcfZOqeSn4RayE9k-pGFkjYfzwLDHwvQCK8BGAsYHg/s0/2020-11-11.jpg" width = "800" height = "480">

*fig3. System Diagram*



| Dec. 	| A 	| B 	| C 	| D 	| a 	| b,c 	| d,e,f 	| g 	|
|------	|---	|---	|---	|---	|---	|-----	|-------	|---	|
| 0    	| 0 	| 0 	| 0 	| 0 	| 0 	|  0  	|   0   	| 0 	|
| 1    	| 0 	| 0 	| 0 	| 1 	| 1 	|  0  	|   0   	| 0 	|
| 2    	| 0 	| 0 	| 1 	| 0 	| 0 	|  1  	|   0   	| 0 	|
| 3    	| 0 	| 0 	| 1 	| 1 	| 1 	|  1  	|   0   	| 0 	|
| 4    	| 0 	| 1 	| 0 	| 0 	| 0 	|  0  	|   1   	| 0 	|
| 5    	| 0 	| 1 	| 0 	| 1 	| 1 	|  0  	|   1   	| 0 	|
| 6    	| 0 	| 1 	| 1 	| 0 	| 0 	|  1  	|   1   	| 0 	|
| 7    	| 0 	| 1 	| 1 	| 1 	| 1 	|  1  	|   1   	| 0 	|
| 8    	| 1 	| 0 	| 0 	| 0 	| 0 	|  0  	|   0   	| 1 	|
| 9    	| 1 	| 0 	| 0 	| 1 	| 1 	|  0  	|   0   	| 1 	|

*fig4. Truth table* 

### Criteria C: Development
```.C++
int led_a = 13; 
int led_b = 12;
int led_d = 11;
int led_g = 10;
int btn_A = 5; #red
int btn_B = 6; #yellow
int btn_C = 7; #green
int btn_D = 8; #blue

int val_A = 0;
int val_B = 0;
int val_C = 0;
int val_D = 0;


void setup()
{
  pinMode(led_a, OUTPUT);
  pinMode(led_b, OUTPUT);
  pinMode(led_d, OUTPUT);
  pinMode(led_g, OUTPUT);
}

void loop()
{
  val_A = digitalRead(btn_A);
  val_B = digitalRead(btn_B);
  val_C = digitalRead(btn_C);
  val_D = digitalRead(btn_D);
  int a = (!val_A)&&(val_D)||((val_A)&&(!val_B)&&(!val_C)&&(val_D));
  digitalWrite(led_a,a);
  

  int b = (!val_A)||(val_C);
  digitalWrite(led_b,b);
  
  int d = (!val_A)&&(val_B);
  digitalWrite(led_d,d);
  
  int g = ((val_A)&&(!val_B))||(!val_C)
  digitalWrite(led_g,g);
  
  
}
```

<img src = "https://github.com/cathymonkey/Unit2/blob/main/display.jpeg" width = "600" height = "480">  

*fig5. Real display 1* 


<img src = "https://github.com/cathymonkey/Unit2/blob/main/display%202.jpeg" width = "600" height = "480">  

*fig6. Real display 2*


<img src = "https://github.com/cathymonkey/Unit2/blob/main/circuit.jpeg" width = "600" height = "480">  

*fig7. Circuit*


**Use instructions**

<img src = "https://github.com/cathymonkey/Unit2/blob/main/button_guide.jpeg" width = "400" height = "400">  

*fig8. User guide*


### Criteria D: Functionality
  
### Criteria E：Evaluation












