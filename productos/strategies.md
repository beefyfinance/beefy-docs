# Estrategias

### ¿Qué es la estrategia de un vault?

Las estrategias de los vaults de Beefy son contratos inteligentes modulares que le indican qué activos debe cultivar y dónde deben ser vendidos. Las recompensas se recolectan regularmente, se intercambian por el activo original del vault y se depositan de nuevo para el proceso de agricultura compuesta.

### **¿Quién controla las estrategias?**

Cada vault y enlace de estrategia está codificado, y el código ha sido construido para ser inmutable, por lo que una vez se liberan, se vuelven imparables. Nadie puede modificar los vaults y las estrategias.

Para lanzar una nueva estrategia en cualquier activo, se debe construir un nuevo contrato inteligente tanto de vault como de estrategia.

### **¿Cómo puedo hacer una estrategia?**

Por ahora puedes publicar y discutir tu estrategia en el Discord de Beefy, dentro del canal #strategies, detallando lo que debería comprar/vender/cultivar y cuál es el APY actual. Habrá una plantilla para ayudarte a empezar.

### **¿Qué es el APR y el APY?**

El APR refleja la tasa de interés simple a lo largo de un año, mientras que el APY describe la tasa de interés con el efecto de la capitalización de los intereses.

### **¿Es el APY/365 la forma correcta de determinar las ganancias diarias?**

No, el efecto del interés compuesto es exponencial, no lineal. Un interés compuesto diario del 1% produciría un 3678,34% al año.

### **¿Cómo optimiza Beefy el APY?**

Beefy automatiza todo el proceso de capitalización, haciéndolo lo más cercano posible al óptimo. La frecuencia de capitalización depende de diferentes variables del sistema, como el TLV, el APR y las comisiones de la estrategia.
