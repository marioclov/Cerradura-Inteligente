### Instrucciones detalladas para construir el circuito con Arduino Nano, RFID-RC522, servomotor, LED y fotorresistencia

#### Materiales necesarios:
- 1 Arduino Nano
- 1 Módulo RFID-RC522
- 1 Servomotor
- 1 LED verde
- 1 Fotorresistencia (LDR)
- 1 Resistencia de **10KΩ** (10000Ω) 
- 1 Resistencia de **200Ω**
- 1 Fuente de alimentación de 9V (pila de 9V)
- Cables

---

### **Paso a paso para construir el circuito**:

#### 1. **Conexiones del Módulo RFID-RC522**:
   El módulo RFID-RC522 utiliza el protocolo **SPI** para comunicarse con el Arduino Nano, y sus pines se conectan de la siguiente manera:

   - **SDA (SS)** → Pin **D10** del Arduino Nano.
   - **SCK** → Pin **D13** del Arduino Nano (reloj del bus SPI).
   - **MOSI** → Pin **D11** del Arduino Nano (datos maestro a esclavo).
   - **MISO** → Pin **D12** del Arduino Nano (datos esclavo a maestro).
   - **GND** → Pin **GND** del Arduino Nano.
   - **RST** → Pin **D9** del Arduino Nano (reinicio del módulo RFID).
   - **3.3V** → Pin **3.3V** del Arduino Nano (alimentación del RFID).

   > **Nota**: El pin **GND** se compartirá entre varios componentes, por lo que tendrás que soldar o unir varios cables en ese pin (RFID, LED, fotorresistencia y servomotor).

#### 2. **Conexión del Servomotor**:
   - El **cable naranja** (señal) del servomotor → Pin **D6** del Arduino Nano.
   - El **cable rojo** (alimentación) → Pin **5V** del Arduino Nano (no a 9V).
   - El **cable marrón** (tierra) → Pin **GND** del Arduino Nano.

   > **Nota**: El pin **5V** también se compartirá para alimentar la fotorresistencia.

#### 3. **Conexiones del LED**:
   - El **ánodo** (pierna más larga) del LED verde → A una resistencia de **200Ω**. Luego, conecta la resistencia al pin **D7** del Arduino Nano.
   - El **cátodo** (pierna más corta) del LED → Conéctalo a **GND** del Arduino Nano.

#### 4. **Conexión de la Fotorresistencia (LDR)**:
   - Conecta uno de los terminales de la fotorresistencia a **5V**.
   - El otro terminal de la fotorresistencia se conecta a un extremo de una resistencia de **10KΩ (10000Ω)**.
   - El otro extremo de la resistencia se conecta a **GND**.
   - El punto medio entre la fotorresistencia y la resistencia se conecta al pin **A0** del Arduino Nano para medir el valor de luz.

   > **Nota**: El pin **GND** también se compartirá con el servomotor, el LED y el RFID. Usa cables trenzados o conectores tipo "Y".

#### 5. **Conexión de la fuente de alimentación (pila de 9V)**:
   - El **terminal positivo** de la pila de 9V se conecta a **VIN** en el Arduino Nano.
   - El **terminal negativo** de la pila de 9V se conecta a **GND** del Arduino Nano.

---

### **Identificación de resistencias mediante colores**:

Para identificar las resistencias en el circuito, observa las bandas de colores en ellas:

- **Resistencia de 200Ω** (limitadora para el LED):
   - Bandas de color: **Rojo, Negro, Marrón, Dorado**
   - **Significado**:
     - **Rojo** (2), **Negro** (0), **Marrón** (x10) → 200Ω.
     - **Dorado** indica una tolerancia de ±5%.

- **Resistencia de 10KΩ** (10000Ω) (utilizada en la fotorresistencia):
   - Bandas de color: **Marrón, Negro, Naranja, Dorado**
   - **Significado**:
     - **Marrón** (1), **Negro** (0), **Naranja** (x1000) → 10,000Ω o 10KΩ.
     - **Dorado** indica una tolerancia de ±5%.

---

### **Explicación de la función de cada componente**:

1. **Arduino Nano**: Controla todo el sistema, ejecutando el código que interactúa con el RFID, servomotor, fotorresistencia y LED.
  
2. **RFID-RC522**: Este módulo detecta tarjetas o llaveros RFID y verifica si están autorizados. Si lo están, activa el servomotor para desbloquear la puerta.

3. **Servomotor**: Funciona como una cerradura. Gira 90 grados cuando se detecta una tarjeta RFID autorizada para permitir acceso.

4. **Fotorresistencia (LDR)**: Detecta si la puerta está abierta o cerrada en función de la cantidad de luz que recibe. Si la luz es baja, se entiende que la puerta está cerrada.

5. **LED**: Indica visualmente si el sistema ha detectado y autorizado correctamente una tarjeta RFID.

6. **Resistencias**:
   - **Resistencia de 200Ω**: Protege el LED limitando la corriente que pasa por él.
   - **Resistencia de 10KΩ**: Junto con la fotorresistencia, forma un divisor de voltaje que permite medir la luz.

---

¡Una vez que hayas conectado todo correctamente, sube tu código al Arduino Nano y el sistema debería estar listo para funcionar!
