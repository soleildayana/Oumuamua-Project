# Oumuamua-Project

## Contexto del repositorio

Este repositorio documenta un miniproyecto académico de mecánica celeste enfocado en el estudio dinámico de **1I/ʻOumuamua** mediante herramientas numéricas en Python, con énfasis en el uso de `pymcel`. El trabajo parte de efemérides reales y desarrolla una lectura orbital basada en teoría de dos cuerpos para caracterizar la geometría hiperbólica del objeto, su estado cinemático y su posible dirección de procedencia interestelar.

El notebook principal (`miniproyecto_oumuamua_pymcel.ipynb`) integra una secuencia de análisis reproducible que incluye:

1. Consulta de efemérides heliocéntricas.
2. Extracción y normalización del vector de estado en unidades físicas.
3. Cálculo de elementos orbitales y verificación energética de la órbita hiperbólica.
4. Reconstrucción geométrica de la asíntota de entrada.
5. Visualización de la trayectoria en contexto del Sistema Solar.
6. Extensiones preliminares para contraste observacional.

## Objetivo general

Construir una base técnica clara y reproducible para analizar el comportamiento orbital de ʻOumuamua en el marco gravitacional solar, conectando los resultados numéricos con conceptos centrales del curso de mecánica celeste.

## Objetivos específicos

- Implementar un flujo de trabajo trazable para pasar de efemérides a diagnóstico orbital.
- Relacionar parámetros dinámicos (energía específica, excentricidad, perihelio, dirección asintótica) con interpretación física.
- Establecer una base modular para futuras extensiones del miniproyecto en teoría de dos cuerpos y propagación orbital.

## Alcance técnico actual

- Modelado de primera aproximación en dinámica central solar.
- Uso de funciones de `pymcel` para conversión estado-elementos, propagación y visualización.
- Integración con fuentes astronómicas de efemérides para inicialización realista del problema.

## Enfoque metodológico

El proyecto se desarrolla bajo una estrategia incremental:

1. **Adquisición de datos**: recuperación de estados iniciales desde efemérides.
2. **Caracterización orbital**: obtención de elementos y verificación de consistencia física.
3. **Reconstrucción geométrica**: inferencia de la dirección de llegada a partir de la solución hiperbólica.
4. **Validación cualitativa**: inspección de trayectorias y contraste visual con posiciones planetarias.
5. **Extensión científica**: generación de hipótesis y líneas de trabajo complementarias.

## Estructura del repositorio

- `/README.md`: descripción general, alcance y guía de lectura del proyecto.
- `/miniproyecto_oumuamua_pymcel.ipynb`: notebook principal con desarrollo del caso de estudio.
- `/ideas_miniproyecto_dos_cuerpos.ipynb`: cuaderno de propuestas implementables para ampliar el miniproyecto desde teoría de dos cuerpos.
- `/agents.md`: guía de referencia técnica para uso de `pymcel` en este entorno.

## Ruta recomendada de lectura

1. Revisar este `README.md` para contexto y alcance.
2. Ejecutar el notebook principal para comprender el flujo base del estudio.
3. Continuar con el notebook de ideas para seleccionar una línea de ampliación y convertirla en implementación.

## Líneas de desarrollo previstas

- Propagación de incertidumbre del estado inicial y sensibilidad de la asíntota de entrada.
- Comparación sistemática entre variantes de resolución de la ecuación de Kepler.
- Experimentos de validación de invariantes dinámicos (energía y momento angular) bajo distintas discretizaciones temporales.
- Escenarios de transferencia y encuentro en marco de dos cuerpos como extensiones de diseño orbital.

## Requisitos sugeridos

- Python 3.8+
- `pymcel`
- `numpy`, `scipy`, `matplotlib`, `plotly`, `pandas`, `astropy`, `astroquery`

## Nota de reproducibilidad

Para preservar trazabilidad, se recomienda fijar explícitamente unidades, tolerancias numéricas, ventanas temporales y parámetros físicos en cada experimento, además de documentar toda su configuración en el propio notebook.
