float x,y,z,temp;
void setup()
{
  pinMode(8, INPUT);
  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(A5, INPUT); 
  pinMode(A4, INPUT);
Serial.begin(9600);
}
void loop()
{
  x= digitalRead(8);
  y= analogRead(A5);
  z= analogRead(A4);
  Serial.println(x);
  Serial.println(y);
  Serial.println(z);
  temp = (double)z / 1024;       
  temp = temp * 5;                 
  temp = temp - 0.5;               
  temp = temp * 100;               
  if ( (x>0) )
  {
    if ((y<550)&&(temp>30))
    {
      digitalWrite(5, HIGH);
      digitalWrite(6, HIGH);
    }
    else if((y<550)&&(temp<30))
    {
      digitalWrite(5, HIGH);
      digitalWrite(6, LOW);
    }
    else if((y>550)&&(temp>30))
    {
      digitalWrite(5, LOW);
      digitalWrite(6, HIGH);
    }
    else if((y>550)&&(temp<30))
    {
      digitalWrite(5, LOW);
      digitalWrite(6, LOW);
    }
  }
  else
  {
    digitalWrite(5, LOW);
    digitalWrite(6, LOW);
  }
}
