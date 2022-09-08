# Modelado de una planta fotovoltaica con EMTP-ATP 
Ficheros de simulación de los elementos de una planta fotovoltaica en EMTP-ATP asociados al Trabajo Fin de Máster "Modelado de una planta fotovoltaica con EMTP-ATP".

### Panel fotovoltaico
Simulación propuesta con variación de la tensión de salida del panel fotovoltaico. Lectura de corrientes `I0` e `IPV` y del valor de la resistencia diferencial `RPV0` a lo largo de la simulación. También se calcula la corriente teórica `IPVTEO`, por lo que se puede observar el error cometido por el modelo durante la simulación.

### Convertidor continua-continua *buck-boost*
Respuesta dinámica del convertidor *buck-boost* ante escalón en el ciclo de trabajo. Generación de la señal de disparo del interruptor a partir de la comparación de una señal triangular y una señal variable. Lectura de las corrientes en la bobina y en el diodo y de la tensión a la salida del convertidor.

### Inversor trifásico
Modelado de inversor trifásico a partir de interruptores controlables TACS con diodos reales en antiparalelo. Modulación vectorial a una frecuencia de 6kHz (parámetro configurable en el `MODEL svm`) con consigna dada por una fuente de tensión trifásica ideal (a 50Hz) . Filtro inductivo y red trifásica equilibrada con medida de tensiones de salida del inversor y de corrientes de línea. Se implementa el `MODEL eliminar` para eliminar la componente homopolar de corriente, resultando en las corrientes corregidas `IA2`, `IB2` e `IC2`.

### Sistema de control del inversor
Desarrollo del seguidor de fase en lazo cerrado (PLL). Implementación de los lazos de control en corriente del inversor trifásico en los ejes d y q. Disposición del circuito de potencia modelando el inversor como una fuente de tensión TACS controlable. Se recomienda obviar los primeros `4s` de simulación dado que se produce un fuerte transitorio debido a la diferencia de tensiones entre el inversor y la red en el instante `t=0`.
