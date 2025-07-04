#include <HX711.h>
#define rc1_calibration_factor -7050.0 //-> 힘이 주어지지 않을 때 값 0 되도록 조정
#define rc2_calibration_factor -7050.0 //-> 힘이 주어지지 않을 때 값 0 되도록 조정
#define rc3_calibration_factor -7050.0 //-> 힘이 주어지지 않을 때 값 0 되도록 조정
#define rc4_calibration_factor -7050.0 //-> 힘이 주어지지 않을 때 값 0 되도록 조정

const int rc1_clk = 2;
const int rc1_dout = 3;
const int rc2_clk = 4;
const int rc2_dout = 5;
const int rc3_clk = 6;
const int rc3_dout = 7;
const int rc4_clk = 8;
const int rc4_dout = 9;


HX711 rc1(rc1_dout, rc1_clk);
HX711 rc2(rc2_dout, rc2_clk);
HX711 rc3(rc3_dout, rc3_clk);
HX711 rc4(rc4_dout, rc4_clk);

void setup() {
  Serial.begin(128000);


  rc1.set_scale(rc1_calibration_factor);
  rc2.set_scale(rc2_calibration_factor);
  rc3.set_scale(rc3_calibration_factor);
  rc4.set_scale(rc4_calibration_factor);

  rc1.tare();
  rc2.tare();
  rc3.tare();
  rc4.tare();

}

int rc1_scale, rc2_scale, rc3_scale, rc4_scale;

void loop() {
  rc1_scale = rc1.get_units();
  rc2_scale = rc2.get_units();
  rc3_scale = rc3.get_units();
  rc4_scale = rc4.get_units();
  Serial.print("rc1: ");
  Serial.print(rc1_scale);
  Serial.print("\t");
  Serial.print("rc2: ");
  Serial.print(rc2_scale));
  Serial.print("\t");
  Serial.print("rc3: ");
  Serial.print(rc3_scale);
  Serial.print("\t");
  Serial.print("rc4: ");
  Serial.println(rc4_scale);

  if((rc1_scale+rc2_scale)-(rc3_scale+rc4_scale)>3)
  {
    Serial.println("Move backward");
  }
  else if((rc1_scale+rc2_scale)-(rc3_scale+rc4_scale)<-3)
  {
    Serial.println("Move forward");
  }
  else
  {
    Serial.println("COF correct!");
  }
}
