# Uso de Servo

<br />
<br />

- Código:

<br />

```cp
#include <LiquidCrystal_I2C.h>
#include <Servo.h>

LiquidCrystal_I2C verdecito(0x27,16,2);
Servo chiquito;

void setup() {
  // put your setup code here, to run once:
  verdecito.init();
  verdecito.backlight();
  chiquito.attach(3);
  splash_screen();
}

void splash_screen(){
  verdecito.setCursor(0,0);
  verdecito.print("MIA UNI Sem5");
  verdecito.setCursor(0,1);
  verdecito.print("Cargando");
  for(unsigned char xvar=8;xvar<14;xvar++){
    verdecito.setCursor(xvar,1);
    verdecito.print("O");
    delay(300);
    verdecito.setCursor(xvar,1);
    verdecito.print("o");
    delay(300);
    verdecito.setCursor(xvar,1);
    verdecito.print(".");
    delay(300);
  }
  verdecito.print("OK");
  delay(3000);
  verdecito.clear();
}

void loop() {
  // put your main code here, to run repeatedly:
  unsigned int potenciometro;
  potenciometro = analogRead(0);
  verdecito.setCursor(0,0);
  verdecito.print("ADC CH0:");
  verdecito.print(potenciometro);
  verdecito.print("   ");
  chiquito.write(map(potenciometro,0,1023,0,180));
  verdecito.setCursor(0,1);
  verdecito.print("Servo:");
  verdecito.print(map(potenciometro,0,1023,0,180));
  verdecito.write(0xDF);
  verdecito.print("  ");
}
```


<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
