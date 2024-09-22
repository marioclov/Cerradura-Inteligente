### Instrucciones para construir el circuito con Arduino Nano, RFID-RC522, servomotor, LED y fotorresistencia

#### Materiales necesarios:
- 1 Arduino Nano
- 1 Módulo RFID-RC522
- 1 Servomotor
- 1 LED verde
- 1 Fotorresistencia (LDR)
- 2 resistencias: 10000 Ω (10K) y 200 Ω
- 1 Fuente de alimentación de 9V (pila de 9V)
- Cables y protoboard (opcional)

### Paso a paso para construir el circuito:

#### 1. **Conexión del Arduino Nano:**
   - Coloca el Arduino Nano en tu protoboard para facilitar las conexiones o usa conectores Dupont para conectarlo directamente.

#### 2. **Conexiones del Módulo RFID-RC522:**
   El módulo RFID-RC522 tiene los siguientes pines que se conectan al Arduino Nano:
   - **SDA (SS)** → Pin **D10** del Arduino Nano (Este es el pin de selección del esclavo para SPI).
   - **SCK** → Pin **D13** del Arduino Nano (Este es el pin de reloj SPI).
   - **MOSI** → Pin **D11** del Arduino Nano (Línea de datos maestro a esclavo en SPI).
   - **MISO** → Pin **D12** del Arduino Nano (Línea de datos esclavo a maestro en SPI).
   - **GND** → Conéctalo al pin **GND** del Arduino Nano.
   - **RST** → Pin **D9** del Arduino Nano (Este es el pin de reinicio del módulo RFID).
   - **3.3V** → Conéctalo al pin **3.3V** del Arduino Nano, ya que el módulo RFID-RC522 funciona a 3.3V.

#### 3. **Conexiones del Servomotor:**
   - El **cable naranja** (señal) del servomotor → Pin **D6** del Arduino Nano.
   - El **cable rojo** (alimentación) → Conéctalo al **VCC** de 9V.
   - El **cable marrón** (tierra) → Conéctalo al **GND** del Arduino Nano.

#### 4. **Conexiones del LED:**
   - El **ánodo** (pierna más larga) del LED verde → Conéctalo a una resistencia de **200Ω** y luego al pin **D7** del Arduino Nano.
   - El **cátodo** (pierna más corta) del LED → Conéctalo a **GND** del Arduino Nano.

#### 5. **Conexión de la Fotorresistencia (LDR):**
   - Conecta uno de los terminales de la fotorresistencia a **5V**.
   - Conecta el otro terminal a un extremo de una resistencia de **10000Ω (10K)**.
   - Conecta el otro extremo de la resistencia a **GND**.
   - El punto entre la fotorresistencia y la resistencia (punto medio) se conecta al pin **A0** del Arduino Nano (para leer el valor de la luz).

#### 6. **Conexión de la fuente de alimentación:**
   - Conecta la batería de **9V** al circuito. El terminal positivo se conecta a **VIN** en el Arduino Nano (que regula el voltaje a 5V y 3.3V según sea necesario).
   - El terminal negativo se conecta a **GND**.

### **Diferenciación de las resistencias:**
   - La resistencia de **200Ω** tiene bandas de color: **rojo, negro, marrón, dorado**. Se utiliza para limitar la corriente que pasa por el LED, evitando que se queme.
   - La resistencia de **10KΩ** (10000Ω) tiene bandas de color: **marrón, negro, naranja, dorado**. Esta resistencia se utiliza junto con la fotorresistencia para formar un divisor de voltaje, que permite al Arduino medir la luz.

### ¿Para qué sirve cada componente?

- **Arduino Nano**: Es el cerebro del proyecto, controla los demás componentes y procesa la información del RFID y el sensor de luz.
  
- **RFID-RC522**: Es el sensor que detecta tarjetas o llaveros RFID. Se utiliza para verificar si una tarjeta o llavero es autorizado para activar el servomotor.

- **Servomotor**: Actúa como una cerradura, moviéndose 90 grados para abrir la puerta o barrera cuando se autoriza un acceso mediante una tarjeta RFID.

- **Fotorresistencia (LDR)**: Detecta si la puerta está cerrada o abierta en función de la cantidad de luz que recibe. Si no detecta luz (porque la puerta está cerrada), el sistema vuelve a bloquear el servomotor.

- **LED**: Indica visualmente cuando se ha autorizado el acceso mediante el RFID.

- **Resistencias**: 
   - La de **200Ω** limita la corriente que pasa por el LED para protegerlo.
   - La de **10KΩ** forma parte del circuito de la fotorresistencia, creando un divisor de voltaje para medir la luz.

### Resumen de conexiones clave:
- **Módulo RFID**: Conectado a los pines 10, 9, 13, 11, 12 del Arduino Nano (SPI).
- **Servomotor**: Conectado a D6.
- **LED**: Conectado a D7 con resistencia de 200Ω.
- **Fotorresistencia (LDR)**: Conectada a A0 con una resistencia de 10KΩ.

¡Una vez que hayas conectado todo correctamente, sube tu código al Arduino Nano y el sistema debería estar listo para funcionar!
