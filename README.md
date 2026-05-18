# Diseño de Ecualizador Analógico de 6 Bandas para Piano Eléctrico

<p align="center">
  <img src="PNG/Escudo-UNIS.png" alt="Escudo de la Universidad" width="200">
</p>
<p align="center">
  <em>Universidad del Istmo de Guatemala</em><br>
  <em>Facultad de Ingeniería</em><br>
  <em>Integrated Microelectronic Devices</em>
</p>
<p align="center">
  <em>Diego Fernando Solís López</em><br>
  <em>mayo de 2026</em>
</p>

---

## 📌 Resumen del Proyecto

[span_0](start_span)Diseño e implementación de un ecualizador analógico de seis bandas optimizado específicamente para el espectro de frecuencias de un piano eléctrico[span_0](end_span). [span_1](start_span)[span_2](start_span)[span_3](start_span)Este repositorio destaca por un exhaustivo análisis y modelado previo en **LTspice**, asegurando la viabilidad matemática, el control de impedancias y el comportamiento en frecuencia de los filtros activos Sallen-Key antes de su implementación en hardware[span_1](end_span)[span_2](end_span)[span_3](end_span).

## 🔬 Análisis y Simulación en LTspice

El núcleo de validación de este proyecto se basó en el uso de simulación SPICE para definir y comprobar los parámetros óptimos del circuito de audio:

* **Optimización de Ancho de Banda:** Se simuló y comparó la respuesta de los filtros utilizando 1 octava frente a 2 octavas. [span_4](start_span)[span_5](start_span)[span_6](start_span)LTspice demostró que el ancho de 2 octavas reduce significativamente la atenuación en la frecuencia central (alcanzando -0.45 dB) y evita problemas de solapamiento en las regiones de transición[span_4](end_span)[span_5](end_span)[span_6](end_span).
* **[span_7](start_span)Simulación AC de Múltiples Etapas:** Se modelaron las 6 ramas pasabanda activas operando de manera simultánea utilizando el modelo del amplificador operacional TL081, validando las frecuencias de corte integrales de todo el sistema[span_7](end_span).
* **Validación del Sumador Inversor:** Se utilizó análisis de barrido AC para comprobar los límites operativos de la etapa de mezcla. [span_8](start_span)[span_9](start_span)Se verificaron matemáticamente los escenarios extremos de ganancia (+12 dB y -12 dB) y el punto de ganancia unitaria (0 dB) al variar los potenciómetros[span_8](end_span)[span_9](end_span).
* **[span_10](start_span)Análisis Individual de Filtros:** Simulación aislada de los filtros pasa-altas (HP2) y pasa-bajas (LP2) para confirmar respuestas tipo Butterworth ($Q \approx 0.707$) con banda de paso máximamente plana[span_10](end_span).

## ⚙️ Arquitectura del Sistema

[span_11](start_span)El flujo de la señal está dividido en cuatro etapas principales modeladas individualmente[span_11](end_span):

1. **[span_12](start_span)[span_13](start_span)Buffer de Entrada:** Seguidor de voltaje para asegurar alta impedancia y evitar cargar las pastillas/salida del piano eléctrico[span_12](end_span)[span_13](end_span).
2. **[span_14](start_span)[span_15](start_span)Etapa de Filtrado (4to Orden):** 6 ramas en paralelo, cada una compuesta por la conexión en cascada de un filtro pasa-altas y un pasa-bajas Sallen-Key[span_14](end_span)[span_15](end_span).
3. **[span_16](start_span)[span_17](start_span)Control de Ganancia (Sumador Activo):** Amplificador operacional en configuración inversora que mezcla las señales filtradas con ajuste independiente por banda[span_16](end_span)[span_17](end_span).
4. **[span_18](start_span)[span_19](start_span)Etapa de Potencia:** Diseño en clase AB con transistores BJT para excitar de forma segura una carga final (bocina de $8\ \Omega$, 35 W)[span_18](end_span)[span_19](end_span).

## 📊 Especificaciones de Bandas de Frecuencia

[span_20](start_span)[span_21](start_span)Frecuencias centrales calculadas mediante media geométrica, implementando un ancho de paso de dos octavas[span_20](end_span)[span_21](end_span):

| Banda | Frecuencia Central | Rango de Operación | Enfoque Acústico |
| :---: | :---: | :---: | :--- |
| **1** | 57 Hz | 28.5 Hz - 114 Hz | [span_22](start_span)[span_23](start_span)Controla la profundidad y peso de graves[span_22](end_span)[span_23](end_span). |
| **2** | 127 Hz | 63.5 Hz - 254 Hz | [span_24](start_span)[span_25](start_span)Cuerpo principal del instrumento; ajusta calidez[span_24](end_span)[span_25](end_span). |
| **3** | 316 Hz | 158 Hz - 632 Hz | [span_26](start_span)[span_27](start_span)Mejora la claridad general (evita sonido "encajonado")[span_26](end_span)[span_27](end_span). |
| **4** | 886 Hz | 443 Hz - 1772 Hz | [span_28](start_span)[span_29](start_span)Determina la definición y presencia en la mezcla[span_28](end_span)[span_29](end_span). |
| **5** | 2121 Hz | 1060.5 Hz - 4242 Hz | [span_30](start_span)[span_31](start_span)Define la articulación y el detalle del ataque del martillo[span_30](end_span)[span_31](end_span). |
| **6** | 4900 Hz | 2450 Hz - 9800 Hz | [span_32](start_span)[span_33](start_span)Controla el brillo, aire y armónicos superiores[span_32](end_span)[span_33](end_span). |

## 🎛️ Parámetros de Control de Ganancia

[span_34](start_span)La simulación definió valores estrictos en la etapa sumadora para evitar saturación del operacional ($|A_{v}| \rightarrow \infty$) mediante resistencias de protección[span_34](end_span):

* **[span_35](start_span)Rango Operativo por Banda:** $\pm 12\text{ dB}$[span_35](end_span).
* **[span_36](start_span)Resistencia de Realimentación ($R_f$):** $13.3\text{ k}\Omega$[span_36](end_span).
* **[span_37](start_span)Resistencia Serie Mínima ($R_s$):** $3.3\text{ k}\Omega$[span_37](end_span).
* **[span_38](start_span)[span_39](start_span)Potenciómetro por Banda ($R_p$):** $50\text{ k}\Omega$ lineal[span_38](end_span)[span_39](end_span).
* *[span_40](start_span)Nota Técnica:* El punto neutro ($0\text{ dB}$) ocurre a los $10\text{ k}\Omega$ del recorrido mecánico, demostrando un ajuste no lineal deseable[span_40](end_span).

## 📂 Archivos del Repositorio

| Directorio / Archivo | Descripción |
| :--- | :--- |
| `/Simulaciones_LTspice/` | Archivos `.asc` y gráficos de respuesta en frecuencia AC de cada banda y de la etapa de suma. |
| `Informe_Ecualizador.pdf` | Documentación teórica, memoria de cálculo de componentes y justificación acústica. |

## 🛠️ Herramientas Utilizadas

* **[span_41](start_span)[span_42](start_span)LTspice:** Plataforma base para el análisis AC y modelado de respuesta en frecuencia[span_41](end_span)[span_42](end_span).
* **[span_43](start_span)[span_44](start_span)Okawa-denshi:** Herramienta de cálculo avanzado para los componentes pasivos de las etapas Sallen-Key[span_43](end_span)[span_44](end_span).
