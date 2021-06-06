```
#include <Arduino.h>
#define RXD2 16
#define TXD2 17
void setup()
{
Serial.begin(115200);
Serial2.begin(9600, SERIAL_8N1, RXD2, TXD2);
Serial.println("Serial Txd is on pin: "+String(TX));
Serial.println("Serial Rxd is on pin: "+String(RX));
}
void loop()
{
while (Serial2.available())
{
Serial.print(char(Serial2.read()));
}
while (Serial.available())
{
Serial2.print(char(Serial.read()));
}
}

```
## Funcionamiento
Dentro del void setup()  inicializa una comunicación en serie a una
velocidad de 115200 bauds (bits por segundo), utilizamos el Serial port 2, y en este
caso establecemos la velocidad de datos a 9600 bauds, también especificamos el protocolo.  Para
finalizar imprimimos por pantalla en que pines están Serial Txd y Serial Rxd.
A continuación empezamos el void loop() , hacemos un while que comprueba si el
Serial2 está disponible, si es así tiene que hacer un print de lo que lee, que lo envié al otro puerto (al
Serial) y lo que le llegue al puerto (al Serial) que lo envié al monitor. el segundo while hace lo mismo
que el primero, pero este comprueba si el Serial esá disponible (no el Serial2).
## salida por el terminal

Por el terminal se ve el siguiente mensaje:
Serial Txd is on pin: 1
Serial Rxd is on pin: 3
...
Yse puede escribir lo que quieras a continuación de estos dos mensajes