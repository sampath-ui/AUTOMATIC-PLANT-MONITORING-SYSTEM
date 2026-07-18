# AUTOMATIC-PLANT-MONITORING-SYSTEM
This project is an Arduino-based Automatic Plant Monitoring System designed to track environmental conditions and automate irrigation for healthy plant growth. It integrates multiple sensors with a microcontroller to monitor soil moisture, temperature, and light intensity, and controls a motor/pump to water plants when needed.


code:-


int soil=A0;
int ldr=A1;
int temp=A3;
int motor=6;
int soilv,ldrr,tempp;


void setup()
{
  pinMode(soil,INPUT);
  pinMode(ldr,INPUT);
  pinMode(temp,INPUT);
  pinMode(motor,OUTPUT);
  Serial.begin(9600);
}

void loop()
{
  //soil moisture
  soilv=analogRead(soil);
  soilv=map(soilv,0, 876, 0, 100);
  Serial.print("soil =");
  Serial.println(soilv);
  delay(1000);
  
  //light measurment
  ldrr=analogRead(ldr);
  ldrr=map(ldrr, 0, 679, 0, 100);
  Serial.print("ldr = ");
  Serial.println(ldrr);
  delay(1000);
  
  
  //temperature
  tempp=analogRead(temp);
  tempp=map(tempp, 0, 872, -40,125);
  Serial.print("tempp =");
  Serial.println(tempp);
  delay(1000);
  
  
  
  
  if (soilv < 25)
  {
    digitalWrite(motor, HIGH);
    Serial.println("Motor ON"); 
  }
  else
  {
    digitalWrite(motor, LOW);
    Serial.println("Motor OFF");
  }

}
