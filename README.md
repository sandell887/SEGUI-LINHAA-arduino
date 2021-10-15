# SEGUI-LINHAA-arduino
programção de segui linha 





<!---programing-->


#include <AFMotor.h>



boolean b_Sensor_Derecho;
boolean b_Sensor_Izquierdo;

AF_DCMotor motorshield_dc_1(1);
AF_DCMotor motorshield_dc_2(2);

void setup()
{
  pinMode(A3, INPUT);
  pinMode(A5, INPUT);
  motorshield_dc_1.run(RELEASE);
  motorshield_dc_2.run(RELEASE);


}


void loop()
{

  b_Sensor_Derecho = digitalRead(A3);
  b_Sensor_Izquierdo = digitalRead(A5);
  if ((b_Sensor_Derecho) && (!b_Sensor_Izquierdo)) {
    motorshield_dc_1.run(BACKWARD);
    motorshield_dc_2.run(FORWARD);
    motorshield_dc_1.setSpeed(130);
    motorshield_dc_2.setSpeed((130));

  }
  if ((!b_Sensor_Derecho) && (b_Sensor_Izquierdo)) {
    motorshield_dc_1.run(FORWARD);
    motorshield_dc_2.run(BACKWARD);
    motorshield_dc_1.setSpeed(130);
    motorshield_dc_2.setSpeed((130));

  }
  if ((!b_Sensor_Derecho) && (!b_Sensor_Izquierdo)) {
        motorshield_dc_1.run(FORWARD);
    motorshield_dc_2.run(FORWARD);
    motorshield_dc_1.setSpeed(55);
    motorshield_dc_2.setSpeed((55));

  }
  if ((b_Sensor_Derecho) && (b_Sensor_Izquierdo)) {
    motorshield_dc_1.run(RELEASE);
    motorshield_dc_2.run(RELEASE);
    motorshield_dc_1.setSpeed(0);
    motorshield_dc_1.setSpeed(0);

  }

}
