
# Astro Communication System 
### Created by Kien Le Trung, Timur Garifullin, Chengyu Fan


## Criteria A: Planning
### Context of the product
We are creating a communication system that could send and receive messages between Earth and arguably any planet. In our case, we are designing our system for austronauts on the moon. The system lets astronaut push buttons to send their messages in English. The system will then convert this into Morse code to show these message through a LED light. Morse-English translating system created by other developers could then be used to read the messages the austronat sent from our system.


#### Sketches of Ideas
Fig 1 is the sketch of how our communication system works. 

<img src ="https://github.com/BrightChanges/Unit-2/blob/main/IMG_7520.JPG" width = "600" height = "400">
Fig.1 Our sketch for how our system looks like


## Criteria B: Design
#### System Diagram
In Fig 2. below, we can clearly see how our system processes. 

<img src ="https://github.com/cathymonkey/Unit2/blob/main/System_diagram.png" width = "600" height = "360">
Fig.2 The system diagram of our program

#### Flow Diagram
Fig.3 is the flow diagram for our system. It's a useful guide for us to code and it always keeps our thinking clear.

![](https://github.com/BrightChanges/Unit-2/blob/main/Astro%20Commun%20Syst%20Flow%20chart.png)
Fig.3 Flow diagram of our complete system
(Link to our Flow Diagram online: https://app.lucidchart.com/lucidchart/invitations/accept/c567ebac-a171-4df8-b23b-e091a7f7a6d5)


## Criteria C: Development
1st development story:

-In the beginning, our team were thinking of creating a selector that constantly hovering over every inputs. We thought that our idea is very cool and advanced. However, due to the limitation of the LCD, which can't show two symbols in the same digit box, we couldn't implement our idea. We felt really sad and we struggled for a while. Despite this difficulties, we worked together and overcame it. We came up with another idea for the selector. Instead of letting the selector to hover around the inputs, we make the location of the selector unchanged, put it in the second row, and we let the inputs move around on the first row. This story shows us that we will meet a lot of problems while developing any system. However, it also shows that if we works together and combine our skills, we will overcome it.

#### Codes (so far):

1. This part focuses on the LCD display function of our communication system including the button function.
```cpp



// include the library code:
#include <LiquidCrystal.h>

//connecting pins of the LCD display
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 10, d7 = 9;

//connecting pins of buttons
const int but_A = 2;
const int but_B = 3;

int ButB_status = 0;
int row_changed = 0;

//connecting pins of the LED
int lightbulb = 7;

//Creating arrays for the letters, numbers and commands
String letters[] = {"a","b","c","d","e","f","g","h","i","j","k","l","m","n","o","p","q","r","s","t","u","v","w","x","y","z"};
String numbers[] = {"0","1","2","3","4","5","6","7","8","9"};
String commands[] = {"_","D","S"}; 

//Variable to interact with the arrays
int letter_showing = 0;
int number_showing = 0;


//variables for the Mode 2 
int ButB_status2 = 0;
int reset = 0;
int command_showing = 0;

// mode status variable 
int mode = 0; //0 - mode 1, 1 - mode 2

//Initializing LCD display 
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
String msg = "";


//Custom character - arrow
byte arrow[8] = {
  0b00000,
  0b00100,
  0b01110,
  0b10101,
  0b00100,
  0b00100,
  0b00100,
  0b00000
};


void setup() {
  Serial.begin(9600);

  //Setup message:
  lcd.begin(16, 2);
  lcd.print("Initializing...");
  delay(800);
  lcd.setCursor(0,1);
  lcd.print("Welcome");
  delay(1000);
  lcd.clear();
  
  pinMode(lightbulb, OUTPUT); 

  //Setup interruptions
  attachInterrupt(0,buttonA, RISING); //Pin 2
  attachInterrupt(1,buttonB, RISING); //Pin 3
  
  lcd.createChar(0,arrow);
  lcd.setCursor(0, 1);  

  //For mode 2
  lcd.setCursor(3,1);  //ButB_status2 = 0
  lcd.print("_");  // show space function
  
}

void loop(){
  lcd.clear();

  //Printing all important data(variables) into the serial monitor. It was used to debug the code .
  
  Serial.print("mode: ");
  Serial.print(mode);
  Serial.print(" Button B mode: ");
  Serial.print(ButB_status);
  Serial.print(" Reset: ");
  Serial.print(reset);
  Serial.print(" row changed: ");
  Serial.print(row_changed);
  Serial.print(" msg: ");
  Serial.println(msg);  
  
  //Printing user interfece on the LCD.
  
  lcd.setCursor(0,1);
  lcd.write(arrow[0]);  
  lcd.setCursor(1,1);
  lcd.print("C");
  lcd.setCursor(2,1);
  lcd.print(":");
  lcd.setCursor(4,1);
  lcd.print(":");
   
  //Checking if two buttons were pressed at the same time(to switch the mode). 
  //Was done by using an AND gate
  
  if(digitalRead(6) == HIGH){
   
    Serial.print("button A, B are pressed。 Mode ");
    Serial.println(mode);
    mode +=1;
    if(mode == 2){
      mode = 0;
    } 
  } 

  
 //Normally scrolling through the alphabet
 if(ButB_status == 0 && mode == 0){
    //Selector scrolling
   	lcd.setCursor(0,0);
    lcd.print(letters[letter_showing]);
   
    //Rest of the alphabet
    lcd.setCursor(2,0);
    for(int i=letter_showing+1; i<26;i++){
         lcd.print(letters[i]);
    }
  }
  
  
  
  //First press of the button
  //Go to letter "O"
  if(ButB_status == 1){
    
    //Selector scrolling
    lcd.setCursor(0,0);
    lcd.print(letters[letter_showing]);
    
    //Rest of the alphabet
    lcd.setCursor(2,0);
    for(int i=letter_showing+1; i<26;i++){
         lcd.print(letters[i]);
    }

  }
  
  
  //Second press
  //Show and scroll through the numbers
  if(ButB_status == 2){
    //Selector scrolling
    
    lcd.setCursor(0,0);
   
    lcd.print(numbers[number_showing]);
    
    //Rest of the numbers
    lcd.setCursor(2,0);
    for(int n = number_showing+1; n < 10; n++){
      	lcd.print(numbers[n]);
    }
  }
  
  
    //print next character
    letter_showing++; 
    number_showing++;
  //Serial.print("Letter showing = ");
  //Serial.println(letter_showing);
  
   //reset the alphabet(letter array)
   if(letter_showing == 27){
      letter_showing = 0;
   } 
  
   //reset numbers(numbers array)
   if (number_showing > 10){
        number_showing = 0;
    }

  if(ButB_status == 1&& letter_showing >27){
    letter_showing = 14; 
   }

  
// Button B Mode 1
    //Make a delay if the row changed
    if(row_changed == 1){
        delay(1000);
        row_changed = 0;
    }



// Codes for BUTTON B IN MODE 2 
  // Changing the commands per click of Button B in mode 2
  
 if(mode == 1){
   if(ButB_status2 == 0 && reset == 1){
      reset = 0;
  	  command_showing = 0; 
      //Serial.println("command_showing = _ ");
      //Serial.println(command_showing); 
      lcd.setCursor(3,1);
      lcd.print(commands[command_showing]); //show space function
  }
}   
  if(ButB_status2 == 0){
      //Serial.println("command_showing = _");
      //Serial.println(command_showing); 
      lcd.setCursor(3,1);
      lcd.print(commands[command_showing]); //show delete function
  } 
  if(ButB_status2 == 1){
      //Serial.println("command_showing = D");
      //Serial.println(command_showing); 
      lcd.setCursor(3,1);
      lcd.print(commands[command_showing]); //show delete function
  }                        
  if(ButB_status2 == 2){ 
      //Serial.println("command_showing = S");
      //Serial.println(command_showing);
      lcd.setCursor(3,1);
      lcd.print(commands[command_showing]); //show send function
    }
  if(ButB_status2 == 3){
      command_showing = 0;
      ButB_status2 = 0;
      reset++;
      //Serial.println("reset");
      //Serial.println(command_showing);
	}

    //show the current message
    lcd.setCursor(5,1);
    lcd.print(msg);
    
    //time between each character
    delay(800);

}

//Functions:

void buttonA(){
  
  if(mode == 0){
   //Serial.println("ButtonA in mode 1 was pressed");
  
    if(ButB_status == 2){
    	 msg += numbers[number_showing-1];
   } 
   else{
    msg += letters[letter_showing-1];
 	//lcd.setCursor(5,1);
  	//Serial.println(msg);
  	//lcd.print(msg);
    }
  }  
  

if(mode == 1){
  Serial.println("ButtonA in mode 2 was pressed");
  Serial.println(command_showing);
  
  //Functions SPACE, DELETE, SEND
  if(command_showing == 0){
      Serial.println("Space");     
      msg += " ";
     
    }
  if(command_showing == 1){
     Serial.println("Delete");
      msg.remove(msg.length()-1);
      
    }
   
   if(command_showing == 2){
      lcd.clear();
      lcd.setCursor(5,1);
      lcd.print("Sending");
      delay(1000);      
      send();
    }
}
  
} //End void
void buttonB(){
  
  
//Mode 1  
	if(mode == 0){
   //Change the row.
    	ButB_status ++;
    	row_changed ++;
  

  	if(ButB_status == 1){
    	letter_showing = 14; 
   	}
  	if(ButB_status == 2){
    	number_showing = 0;
  	}
         
  	if(ButB_status == 3){
      	letter_showing = 0;
      	ButB_status = 0;
    }
      
    
} 
  
  
//Mode 2    
if(mode == 1){
  ButB_status2++;
  command_showing++;
  //check if the mode is 2
  Serial.println(" Mode 2 ");
  Serial.print("ButB_status2 = ");  
  Serial.println(ButB_status2);  
    

  }
}

```

2. The second part of the code focuses on the sending function and the LED message. We also create code for converting English text(input) to morse code.
```cpp

//English to morse
void dash(){
  Serial.println("dash function");
  digitalWrite(lightbulb,HIGH);
  delay(30000);
  digitalWrite(lightbulb,LOW);
  delay(10000);
}

void dot(){
  Serial.println("dot function");
  digitalWrite(lightbulb,HIGH);
  delay(10000);
  digitalWrite(lightbulb,LOW);
  delay(10000);
}

void send(){
  Serial.println("sending");
  Serial.print("Message = ");
  Serial.println(msg);
  for(int i=0; i<msg.length();i++){
    Serial.println(msg[i]);
    if(msg[i]=='a'){
       Serial.println("Morse A");
    	dot();
        dash();
    }
    if(msg[i]=='b'){
      Serial.println("Morse B");
    	dash();
      	dot();
      	dot();
      	dot();
    }
    if(msg[i]=='c'){
      Serial.println("Morse C");
    	dash();
        dot();
        dash();
        dot();
    }
    if(msg[i]=='d'){
      Serial.println("Morse D");
    	dash();
      	dot();
      	dot();
    }
    if(msg[i]=='e'){
      Serial.println("Morse E");
      	dot();
    }
    if(msg[i]=='f'){
      Serial.println("Morse F");
      	dot();
      	dot();
      	dash();
      	dot();
    }
    if(msg[i]=='g'){
      Serial.println("Morse G");
      	dash();
      	dash();
      	dot();
    }
    if(msg[i]=='h'){
      Serial.println("Morse H");
      	dot();
      	dot();
      	dot();
      	dot();
    }
    if(msg[i]=='i'){
      Serial.println("Morse I");
      	dot();
      	dot();
    }
    if(msg[i]=='j'){
      Serial.println("Morse J");
      dot();
      dash();
      dash();
      dash(); 
    }
    if(msg[i]=='k'){
      Serial.println("Morse K");
      dash();
      dot();
      dash();
    }
    if(msg[i]=='l'){
      Serial.println("Morse L");
      dot();
      dash();
      dot();
      dot();
      
    }
    if(msg[i]=='m'){
      Serial.println("Morse M");
      dash();
      dash();
    }
    if(msg[i]=='n'){
      Serial.println("Morse N");
      dash();
      dot();
    }
    if(msg[i]=='o'){
      Serial.println("Morse O");
      dash();
      dash();
      dash();
    }
    if(msg[i]=='p'){
      Serial.println("Morse P");
      dot();
      dash();
      dash();
      dot();
    }
    if(msg[i]=='q'){
      Serial.println("Morse Q");
      dash();
      dash();
      dot();
      dash();
    }
    if(msg[i]=='r'){
      Serial.println("Morse R");
      dot();
      dash();
      dot();
    }
    if(msg[i]=='s'){
      Serial.println("Morse S");
      dot();
      dot();
      dot();
    }
    if(msg[i]=='t'){
      Serial.println("Morse T");
      dash();
    }
    if(msg[i]=='u'){
      Serial.println("Morse U");
      dot();
      dot();
      dash();
    }
    if(msg[i]=='v'){
      Serial.println("Morse V");
      dot();
      dot();
      dot();
      dash();
    }
    if(msg[i]=='w'){
      Serial.println("Morse W");
      dot();
      dash();
      dash();
    }
    if(msg[i]=='x'){
      Serial.println("Morse X");
      dash();
      dot();
      dot();
      dash();
    }
    if(msg[i]=='y'){
      Serial.println("Morse Y");
      dash();
      dot();
      dash();
      dash();
    }
    if(msg[i]=='z'){
      Serial.println("Morse Z");
      dash();
      dash();
      dot();
      dot();
    }
    if(msg[i]=='1'){
      Serial.println("Morse 1");
      dot();
      dash();
      dash();
      dash();
      dash();
    }
    if(msg[i]=='2'){
      Serial.println("Morse 2");
      dot();
      dot();
      dash();
      dash();
      dash();
    }
    if(msg[i]=='3'){
      Serial.println("Morse 3");
      dot();
      dot();
      dot();
      dash();
      dash();
    }
    if(msg[i]=='4'){
      Serial.println("Morse 4");
      dot();
      dot();
      dot();
      dot();
      dash();
    }
    if(msg[i]=='5'){
      Serial.println("Morse 5");
      dot();
      dot();
      dot();
      dot();
      dot();
    }
    if(msg[i]=='6'){
      Serial.println("Morse 6");
      dash();
      dot();
      dot();
      dot();
      dot();
    }
    if(msg[i]=='7'){
      Serial.println("Morse 7");
      dash();
      dash();
      dot();
      dot();
      dot();
    }
    if(msg[i]=='8'){
      Serial.println("Morse 8");
      dash();
      dash();
      dash();
      dot();
      dot();
    }
    if(msg[i]=='9'){
      Serial.println("Morse 9");
      dash();
      dash();
      dash();
      dash();
      dot();
    }	
    if(msg[i]=='0'){
      Serial.println("Morse 0");
      dash();
      dash();
      dash();
      dash();
      dash();
    }   
    delay(30000);
    
  }
}
```
2st development story:-Creating this system for us were overall a very challenging experience for all members in our team. We were very new to coding in C++ and doing things related to Arduino, especially the LCD.

![](https://github.com/cathymonkey/Unit2/blob/main/Astro_CommunicationSystem/real-life%20model.png)
Fig.3 Our system model on TinkerCad

## Criteria D: Functionality
#### Real-life program
Link to the desmontration video (with us going through Alpha test for our success criterias):
Video 1: https://www.youtube.com/watch?v=J7-qxpr3GQE
Video 2: https://www.youtube.com/watch?v=p6FbCQ4yoOI&ab_channel=KienLeTrung


![](https://github.com/BrightChanges/Unit-2/blob/main/IMG_5498.JPG)
Fig.4 Picture of our system

![](https://github.com/BrightChanges/Unit-2/blob/main/New%20Project%20(71).png)
Fig.5 Intruction set for our system


## Criteria E: Evaluation

##### Success Criteria
| Criteria:                                                                                                      | Expected outcome                                                                                                   | Met? |
|----------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|------|
| Criteria 1: The user should be able to input  alphabetic characters and numbers(0-9).                          | You are able to input alphabetic characters  and numbers(0-9) into the system.                                     |      |
| Criteria 2: It should output the user's message  on the LCD and through with light(Using Morse code)           | You are able to see how your message is  outputed on the LCD and the light is blinking  according to a Morse code. |      |
| Criteria 3: It should let the user use the  following commands: send message, delete,  space, repeat, confirm. | You are able to use the following commands:  send message, delete, space, repeat, confirm.                         |      |
| Criteria 4: It should provide an instruction set.                                                              | You are able to see how to use our system with  different button combinations.                                     |      |
| Criteria 5: It should let the user type at least 10 words in 1 minute                                          | You are able to type at least 10 words in 1 minute.                                                                |      |
| Criteria 6: It should contain at most  2 buttons and 1 LED.                                                    | You are able to see that our system contains at most 2 buttons and 1 button.                                       |      |


