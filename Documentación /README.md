# Documentación Técnica - Ecualizador Analógico de 6 Bandas

Este directorio contiene la memoria de cálculo y la justificación teórica del diseño de un ecualizador analógico de seis bandas, optimizado para el espectro de frecuencias de un piano eléctrico.

## 📄 Contenido del Informe

El archivo principal de esta carpeta es `Ecualizador .pdf`, el cual detalla paso a paso la ingeniería detrás del hardware:

* **Arquitectura del Sistema:** Desglose de las cuatro etapas del circuito (Buffer de entrada, Etapa de filtrado Sallen-Key, Control de ganancia y Etapa de potencia).
* **Definición de Frecuencias:** Justificación acústica y cálculo matemático de las frecuencias centrales utilizando la media geométrica.
* **Optimización de Ancho de Banda:** Análisis comparativo que demuestra por qué se amplió el ancho de banda a dos octavas para evitar caídas de ganancia severas en las frecuencias centrales (reduciendo la atenuación a -0.45 dB).
* **Cálculo de Filtros Activos:** Tablas detalladas con los valores exactos de resistencias y capacitores para los filtros pasa-altas y pasa-bajas de segundo orden (respuesta Butterworth, Q ≈ 0.707).
* **Diseño del Sumador Inversor:** Ecuaciones y selección de componentes comerciales para garantizar un ajuste seguro y simétrico de ±12 dB, evitando la saturación del amplificador operacional.

## 📊 Parámetros Clave Calculados

* **Frecuencias Centrales (f0):** 57 Hz, 127 Hz, 316 Hz, 886 Hz, 2121 Hz, 4900 Hz.
* **Sumador - Resistencia de Realimentación (Rf):** 13.3 kΩ.
* **Sumador - Resistencia Serie Mínima (Rs):** 3.3 kΩ.
* **Sumador - Potenciómetro por Banda (Rp):** 50 kΩ lineal.
* **Margen Máximo de Bocina (8 Ω, 35W):** 16.7 VRMS / 24.4 dB de ganancia máxima.