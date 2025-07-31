const int motorPin = 11;
const int temPin = A0;
const int gPin = 6;
const int bPin = 5;
const int rPin = 9;


void setup(){
 pinMode(temPin,INPUT);
 pinMode(rPin, OUTPUT);
 pinMode(bPin, OUTPUT);
 pinMode(gPin, OUTPUT);
 pinMode(motorPin,OUTPUT);
}

void loop(){
 int sv =analogRead(temPin);
 float v = sv *(5.0/1280.0);
 float tempc = (v - 0.5)*100;
 float tempf = (tempc *9.0/5.0)+32;
 sv = constrain(v, 0, 250);
  if(tempf >= 85.0){
    analogWrite(gPin,sv + 12);
    analogWrite(bPin,sv - 18);
    analogWrite(rPin,sv + 12);
    for(int speed = 0; speed <= 50; speed++)
    analogWrite(motorPin,speed);
    delay(50);
  }else{
    analogWrite(rPin, 0);
    analogWrite(gPin, 0);
    analogWrite(bPin, 0);
   analogWrite(motorPin,0);
  } 
}
