## Uso de dos displays

<br />
<br />


- Página para codigo de display: https://jasonacox.github.io/TM1637TinyDisplay/examples/7-segment-animator.html

<br />

- Codigo:

<br />

```cpp
void setup() {
  // put your setup code here, to run once:
  unsigned char x_var;
  for (x_var = 0; x_var < 9; x_var++) {
    pinMode(x_var + 2, OUTPUT);
  }
}

unsigned char datos_UNI[] = {0x79, 0x38};

void write_7S_port(unsigned char dato) {
  unsigned char x_var;
  for (x_var = 0; x_var < 7; x_var++) {
    if (((dato >> x_var) & 0x01) == 1) {
      digitalWrite(x_var + 2, HIGH);
    } else {
      digitalWrite(x_var + 2, LOW);
    }
  }
}

void loop() {

  // Mostrar E en display 1
  write_7S_port(datos_UNI[0]);
  digitalWrite(10, HIGH);
  delay(3);
  digitalWrite(10, LOW);

  // Mostrar L en display 2
  write_7S_port(datos_UNI[1]);
  digitalWrite(9, HIGH);
  delay(3);
  digitalWrite(9, LOW);
}
```


<br />
<br />
<br />
<br />
<br />

