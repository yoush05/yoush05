4/11 
LiqeidCrystal I2C와  SimpleDHT 라이브러리를 이용해 온도센서의 값을 lcd에 프린트하는 프로그램을 작성함 
lcd를 출력하는 프로그램을 이용하여 함
(int) 를 써서 온도를 정숫값으로 출력함 
(char)은 문자를 의미함 
아래 코드는 위에서 설명한 프로그램이다. 


#include <Wire.h> 
#include <LiquidCrystal_I2C.h>
#include <SimpleDHT.h>

int pinDHT11 = 2;
이 코드는 pinDHT11을 2번에 연결했다는 코드이고
SimpleDHT11 dht11(pinDHT11);


LiquidCrystal_I2C lcd(0x27,16,2); 
void setup()
{
  lcd.init();   
    Serial.begin(9600);
  lcd.backlight();
}


void loop()
{Serial.println("=================================");
  Serial.println("Sample DHT11...");
  
  // read without samples.
  byte temperature = 0;
  byte humidity = 0;
  int err = SimpleDHTErrSuccess;
  if ((err = dht11.read(&temperature, &humidity, NULL)) != SimpleDHTErrSuccess) {
    Serial.print("Read DHT11 failed, err="); Serial.print(SimpleDHTErrCode(err));
    Serial.print(","); Serial.println(SimpleDHTErrDuration(err)); delay(1000);
    return;
  }
  여기 코드는 오류가 뜬다면 오류라고 표시하고 아니라면 정상적으로 표시한다는 코드이다.
  Serial.print("Sample OK: ");
  Serial.print((int)temperature); Serial.print(" *C, "); 
  Serial.print((int)humidity); Serial.println(" H");
  
  여기까지가 시리얼프린트를 한 부분이다.
  
   lcd.setCursor(0,0);
   lcd.print("t is ...");
  lcd.print((int)temperature);lcd.print((char)0xDF); lcd.print("C");
  여기서 (char)는 문자를 의미한다. lcd.print((char)0xDF);는 °를 표시하기 위한 코드이다. 
  lcd.setCursor(0,1);
  lcd.print("h is...");
  lcd.print((int)humidity); lcd.print("%");
이제 이부분은 lcd에 표시하는 코드이다. 0,0부터 온도를 표시하고, 0,1에서는 습도를 표시한다
(int)는 온도와 습도를 실수가 아닌 정수값으로 표시하겠다는 의미이다. 
   
  // DHT11 sampling rate is 1HZ.
  delay(1500);

}

이제는 회로에 대해 알아보자. 
회로는 기본적으로 vcc는 5v를 인가하고, 데이터는 2번에 인가했다.
GND는 그대로 GND에 인가했다. 
