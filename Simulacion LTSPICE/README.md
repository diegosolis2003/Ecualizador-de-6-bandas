# Simulación en LTspice - Ecualizador Analógico de 6 Bandas

Este directorio contiene el entorno de validación SPICE para el ecualizador analógico. El archivo principal es `Ecualizador.asc`, el cual integra todas las etapas de filtrado y suma del sistema de audio.

## 🔬 Estructura del Esquemático

El archivo de simulación está diseñado para realizar un análisis de respuesta en frecuencia de extremo a extremo, evaluando tanto las bandas individuales como el comportamiento del sumador activo.

* **Modelos Activos:** Se utilizan modelos de amplificadores operacionales `ADTL084` alimentados con fuentes simétricas de ±12 V para replicar el comportamiento de las etapas Sallen-Key y el sumador.
* **Filtros Sallen-Key (4to Orden):** Implementación de las seis ramas en paralelo (cascada de HP2 y LP2) ajustadas a las frecuencias centrales calculadas (57 Hz a 4.9 kHz) con anchos de banda de dos octavas.
* **Sumador Activo:** Red de resistencias de entrada configurables para simular los potenciómetros en distintas posiciones, probando los límites de ganancia.

## ⚙️ Instrucciones de Ejecución

Para visualizar las curvas de respuesta en frecuencia (Diagramas de Bode):

1. Abre el archivo `Ecualizador.asc` en LTspice.
2. Haz clic en **Run** (el ícono de la persona corriendo en la barra superior).
3. El simulador ejecutará automáticamente la directiva preconfigurada de análisis AC de barrido logarítmico: `.ac dec 1000 20 20k` (1000 puntos por década, desde 20 Hz hasta 20 kHz).

## 📈 Nodos de Medición (Probes) Destacados

Puedes pinchar en las siguientes etiquetas del esquemático para observar las señales de interés en el visor de formas de onda de LTspice:

* `VoutB1` a `VoutB6`: Respuesta individual del filtro pasa-banda de la banda correspondiente (antes del sumador).
* `VoutSum-12dB`: Salida total del sistema con atenuación máxima (Rp = 50 kΩ).
* `VoutSum0dB`: Salida total del sistema con ganancia unitaria (Rp = 10 kΩ).
* `VoutSum+12dB`: Salida total del sistema con amplificación máxima (Rp = 0 Ω).