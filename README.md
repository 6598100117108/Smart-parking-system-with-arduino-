#include<Servo.h>   
Servo gate;        
int slot1 = 5;   
int slot2 = 4;  
int gateSensor = 3;
int slot1_l = 13;
int slot2_l = 12;
int gate_grn = 11;
int gate_red = 10;


void setup() 
{
gate.attach(7);     
pinMode(slot1,INPUT);  
pinMode(slot2,INPUT);
pinMode(gateSensor,INPUT);
 pinMode(slot1_l,OUTPUT);
 pinMode(slot2_l,OUTPUT);
 pinMode(gate_grn,OUTPUT);
 pinMode(gate_red,OUTPUT);
 Serial.begin(9600); 

}

void loop() 
{
 

if(   !(digitalRead(gateSensor)) && digitalRead(slot1) && digitalRead(slot2))   
 {
  Serial.println("Welcome, Available: sLOT1, sLOT2");  
  digitalWrite(slot1_l,HIGH);
  digitalWrite(slot2_l,HIGH);
  delay(1000);
  digitalWrite(gate_grn,HIGH);
  gate.write(75); 
 }

 if( !(digitalRead(gateSensor)) && !(digitalRead(slot1)) && digitalRead(slot2))  
  {
      Serial.println("Welcome, Available: sLOT2");  
      digitalWrite(slot1_l,LOW);
      digitalWrite(slot2_l,HIGH);
      delay(1000);
      digitalWrite(gate_grn,HIGH);
     gate.write(75); 
  }
  
   if( !(digitalRead(gateSensor)) && digitalRead(slot1) && !(digitalRead(slot2)))     
   {
     Serial.println("Welcome, Available: sLOT1");  
      digitalWrite(slot1_l,HIGH);
      digitalWrite(slot2_l,LOW);
      delay(1000);
     digitalWrite(gate_grn,HIGH);
     gate.write(75); 
      delay(100);                
   }
  

    if( !(digitalRead(gateSensor)) && !(digitalRead(slot1)) && !(digitalRead(slot2)))
     {
       Serial.println("Welcome, Parking Full");
        digitalWrite(slot1_l,LOW);
        digitalWrite(slot2_l,LOW);
        delay(1000);
        digitalWrite(gate_red,HIGH);
        delay(100);
        digitalWrite(gate_red,LOW);
        delay(100);
        digitalWrite(gate_red,HIGH);
        delay(100);
        digitalWrite(gate_red,LOW);
        
        
     }
        
if( digitalRead(gateSensor)) 
    { Serial.println("Welcome");  
      gate.write(5);      
     digitalWrite(slot1_l,LOW);
     digitalWrite(slot2_l,LOW);
     digitalWrite(gate_red,LOW);
     digitalWrite(gate_grn,HIGH);
     delay(100);
     digitalWrite(gate_grn,LOW);
     delay(100);
     
    
    }

	}
