# Revisión: *A General Method for Assessing the Origin of Interstellar Small Bodies: The Case of 1I/2017 U1 ('Oumuamua)*

## 1. Información Bibliográfica
- **Título:** A General Method for Assessing the Origin of Interstellar Small Bodies: The Case of 1I/2017 U1 ('Oumuamua)
- **Autores:** Jorge I. Zuluaga, Oscar Sánchez-Hernández, Mario Sucerquia, Ignacio Ferrín
- **Afiliación:** Solar, Earth and Planetary Physics Group & Computational Physics and Astrophysics Group (FACom), Instituto de Física—FCEN, Universidad de Antioquia, Medellín, Colombia
- **Publicación:** *The Astronomical Journal*, Vol. 155, No. 6, 2018 June, Artículo 236 (15 pp.)
- **DOI:** https://doi.org/10.3847/1538-3881/aabd7c
- **Fechas:** Recibido 26 noviembre 2017 / Revisado 8 abril 2018 / Aceptado 9 abril 2018 / Publicado 15 mayo 2018
- **Repositorio de código/datos:** iWander package disponible en http://github.com/seap-udea/iWander

## 2. Contexto y Objetivo del Estudio
El descubrimiento de 1I/2017 U1 ('Oumuamua) en octubre de 2017 mediante el sondeo Pan-STARRS marcó la primera detección confirmada de un objeto con órbita hiperbólica (e = 1.1995 ± 0.0002) y velocidad asintótica de ~26.33 km s⁻¹, estableciendo su origen interestelar. Este hallazgo generó interés en determinar el sistema estelar progenitor del objeto, con implicaciones para comprender los procesos de eyección de planetesimales, la arquitectura de sistemas planetarios extrasolares, y la distribución espacial de objetos interestelares.

El **objetivo específico** de este trabajo es desarrollar una metodología general y cuantitativa para asignar probabilidades de origen interestelar (Interstellar Origin Probabilities, IOP) a estrellas cercanas como posibles sistemas progenitores de un objeto interestelar observado. El estudio se aplica al caso de 'Oumuamua como ejemplo ilustrativo, con el propósito de:
1. Establecer un marco probabilístico riguroso que incorpore explícitamente las incertidumbres en los elementos orbitales del objeto y en los parámetros astrométricos de las estrellas.
2. Implementar una herramienta computacional (iWander) que permita reproducir y actualizar los cálculos conforme mejore la información observacional.
3. Generar una lista preliminar de candidatos progenitores para 'Oumuamua con sus respectivas IOP, identificando aquellos sistemas estelares cuyas propiedades cinemáticas y físicas son compatibles con la eyección del objeto.

## 3. Metodología y Enfoque
- **Tipo de estudio:** Desarrollo metodológico combinado con aplicación numérica, integrando dinámica orbital, estadística bayesiana/frecuentista, y modelado del potencial galáctico.
- **Datos y fuentes:**
  - *Orbita de 'Oumuamua:* Solución nominal y matriz de covarianza de elementos orbitales del JPL Small-Body Database (referencia epoch 2017 Nov 02.0), con 118 observaciones posicionales spanning Oct 14 – Nov 10, 2017.
  - *Catálogo estelar:* AstroRV, compilado por los autores a partir de Gaia TGAS, Hipparcos, Tycho-2, Simbad, y múltiples catálogos de velocidades radiales (WEB1995, GCS, RAVE-DR5, PULKOVO, etc.), conteniendo 285,114 estrellas con astrometría y velocidades radiales completas.
  - *Potencial galáctico:* Modelo axisimétrico de Kuzmin-like con tres componentes (disco, bulbo, halo), siguiendo parámetros de Bailer-Jones (2015) e Irrgang et al. (2013).
- **Procedimiento analítico:**
  1. **Generación de objetos sustitutos (surrogate objects):** Se producen Np = 10,000 realizaciones de los elementos orbitales de 'Oumuamua mediante un generador gaussiano multivariado con media igual a la solución nominal y covarianza igual a la matriz publicada por JPL.
  2. **Integración en el Sistema Solar:** Propagación hacia atrás de las órbitas de los sustitutos usando un integrador Gragg-Bulirsch-Stoer, incluyendo el Sol y los ocho planetas, hasta una distancia de truncamiento tidal dT,☉ = 50,000 au (tiempo de ingreso ting).
  3. **Selección preliminar de candidatos (LMA):** Aplicación de la aproximación de movimiento lineal (Linear Motion Approximation) para identificar estrellas con distancia mínima LMA dLMA,min ≤ dmax = 10 pc, reduciendo el conjunto de ~285,000 a ~2,560 candidatas.
  4. **Integración en el potencial galáctico:** Propagación precisa de las órbitas del objeto nominal y las estrellas candidatas en el potencial galáctico axisimétrico para calcular tiempos y distancias de encuentro refinados (tmin, dmin).
  5. **Generación de estrellas sustitutas (surrogate stars):** Para cada candidata, se generan Ns realizaciones de sus parámetros astrométricos (posición, paralaje, movimiento propio, velocidad radial) compatibles con sus errores reportados.
  6. **Cálculo de la probabilidad de posición (Ppos):** Estimación de la densidad numérica de trayectorias estelares en la posición del objeto en el momento de encuentro mínimo, usando un kernel de suavizado gaussiano con escala h ≈ 0.5 pc.
  7. **Cálculo de la probabilidad de velocidad (f ind):** Modelado de la distribución de velocidades de eyección de cuerpos menores mediante un enfoque semi-analítico inspirado en Wiegert (2011, 2014), asumiendo dispersión gravitacional por planetas gigantes.
  8. **Cálculo de la IOP:** Combinación de Ppos y f ind según la expresión IOP ∝ Npos × f ind, con normalización sobre el conjunto de estrellas consideradas.

## 4. Marco Teórico y Formalismo Matemático Clave
El artículo emplea los siguientes elementos formales:
- **Aproximación de Movimiento Lineal (LMA):** Para partículas con posición ri,0 y velocidad vi en el tiempo t0, la distancia mínima entre dos partículas j y k se calcula analíticamente:
  $$t_{jk,\text{min}} = -\frac{\Delta \vec{r}_{jk,0} \cdot \Delta \vec{v}_{jk,0}}{|\Delta \vec{v}_{jk,0}|^2}, \quad d_{jk,\text{min}} = |\Delta \vec{r}_{jk,0} + \Delta \vec{v}_{jk,0} t_{jk,\text{min}}|$$
  donde Δrjk,0 = rk,0 − rj,0 y Δvjk,0 = vk,0 − vj,0.
- **Transformación de coordenadas galácticas:** Conversión de coordenadas heliocéntricas (xgal, ygal, zgal, U, V, W) a coordenadas galactocéntricas cilíndricas (R, θ, z) para la integración en el potencial, incluyendo correcciones por la posición y velocidad del Sol respecto al LSR.
- **Potencial galáctico axisimétrico:**
  $$\Phi(R,z) = -\sum_{i=d,b,h} \frac{GM_i}{\sqrt{R^2 + (a_i + \sqrt{z^2 + b_i^2})^2}}$$
  con parámetros Mi, ai, bi para disco, bulbo y halo especificados en la Tabla 3 del artículo.
- **Densidad numérica por kernel de suavizado:**
  $$n(\vec{r}_p) = \sum_{i=1}^{N_s} W(|\vec{r}_p - \vec{r}_i^*|, h), \quad W(d,h) = \sigma^{-1} \exp\left(-\frac{d^2}{h^2}\right)$$
  donde σ es una constante de normalización y h ≈ 0.5 pc es la escala de suavizado.
- **Distribución de velocidades de eyección:** Estimación semi-analítica de la distribución posterior de velocidades de exceso v∞ para cuerpos menores dispersados por planetas gigantes, asumiendo priores uniformes en Mp y ap, resultando en una distribución aproximadamente Maxwell-Boltzmann con media dependiente de la masa y distancia orbital del planeta.
- **Factor de corrección por flujo de fondo (f ind):**
  $$f_{\text{ind}}(v_{\text{rel}}) \approx \frac{p_{\text{ind}}(v_{\text{rel}})}{p_B(v_{\text{rel}}) + p_{\text{ind}}(v_{\text{rel}})} \quad \text{(asumiendo } p_B \gg p_{\text{ind}}\text{)}$$
  donde pind y pB son las distribuciones de velocidad para objetos indígenas (eyectados) y de fondo (dispersados), respectivamente.

## 5. Resultados Principales
1. **Identificación de candidatos progenitores:** De las 285,114 estrellas iniciales, el procedimiento identificó 16 "progenitores potenciales" que cumplen tmin,nom ≤ tret ≈ 40 Myr y dmin,nom ≤ 2 pc. Estos se listan en la Tabla 4 del artículo en orden descendente de IOP.
2. **Candidato principal:** HIP 103749 (HD 200325) presenta la IOP más alta, con tmin = −4.22 Myr, dmin = 1.75 pc (rango percentil 10–90: 0.37–4.98 pc), vrel = 12.0 km s⁻¹, y un parámetro de centrado f = 0.55. Es un sistema binario/múltiple con una primaria de masa ~1.19 M☉ y edad ~3.2 Gyr, y una compañera enana K a ~25 au.
3. **Otros candidatos notables:** TYC 3144-2040-1 (d = 4.5 pc, tmin = −0.12 Myr, vrel = 17.9 km s⁻¹), HIP 3821 (η Cas, d = 6.0 pc, tmin = −0.17 Myr, vrel = 23.5 km s⁻¹), y HIP 113020 (GJ 876, d = 3.5 pc, tmin = −0.03 Myr, vrel = 36.8 km s⁻¹) figuran entre los candidatos con IOP significativas.
4. **Índice de calidad astrométrica (q):** Los candidatos presentan valores de q (mínimo ratio entre parámetro astrométrico y su error) entre 1 y 171, indicando que algunos tienen astrometría de alta precisión (ej. HIP 21553 con q = 171) mientras otros tienen incertidumbres mayores (ej. HIP 103749 con q = 1).
5. **Sensibilidad a incertidumbres orbitales:** La propagación de los 10,000 clones de 'Oumuamua produce intervalos de variación en dmin típicamente del orden de ±10–30% para la mayoría de los candidatos, confirmando que las incertidumbres orbitales actuales no invalidan la identificación preliminar de candidatos.
6. **Predicción de tasas de detección futuras:** El artículo menciona que, con la operación completa del LSST/Rubin Observatory, se podrían detectar ~1 objeto interestelar por año, lo que permitiría aplicar esta metodología de manera sistemática a múltiples objetos.

## 6. Discusión y Análisis Descriptivo
El artículo presenta una metodología estructurada para cuantificar la probabilidad de que una estrella cercana sea el sistema progenitor de un objeto interestelar. El enfoque se caracteriza por tratar explícitamente las incertidumbres en ambos lados del problema (objeto y estrella) mediante la generación de ensembles de trayectorias sustitutas, y por separar claramente los componentes de probabilidad de posición y de velocidad.

**Aspectos metodológicos destacados:**
- La distinción entre la probabilidad de coincidencia espacial (Ppos) y la probabilidad condicional de que un encuentro espacial corresponda a un proceso de eyección (f ind) permite incorporar información física sobre los mecanismos de eyección sin asumir que todos los encuentros cercanos son igualmente probables como origen.
- El uso de un kernel gaussiano para estimar densidades numéricas a partir de un conjunto discreto de trayectorias proporciona una estimación continua y diferenciable de Ppos, evitando artefactos discretos en la evaluación de probabilidades.
- La implementación del paquete iWander en C/C++/Python, con scripts de post-procesamiento en iPython notebooks, facilita la reproducibilidad y la actualización de los cálculos conforme mejoren los datos astrométricos (ej. con Gaia DR2/DR3).

**Relación con observaciones de 'Oumuamua:**
- La identificación de HIP 103749 como candidato principal se basa en su combinación de distancia de encuentro moderada (~1.75 pc), velocidad relativa baja (~12 km s⁻¹), y tiempo de encuentro reciente (~4 Myr), factores que son consistentes con mecanismos de eyección por dispersión planetaria.
- La naturaleza binaria de HIP 103749 se menciona como un factor que podría favorecer la eyección de cuerpos menores, dado que sistemas binarios pueden proporcionar mecanismos adicionales de dispersión gravitacional.
- La baja velocidad relativa de 'Oumuamua respecto al LSR (~9 km s⁻¹) se discute en el contexto de que es típica de sistemas estelares jóvenes (<2 Gyr), lo que sugiere que el objeto podría haber sido eyectado de un sistema relativamente joven.

**Contexto en la literatura:**
- El artículo se posiciona como una extensión metodológica de trabajos previos que buscaban identificar el origen de 'Oumuamua mediante propagación orbital simple (Dybczyński & Królikowska 2017; Portegies Zwart et al. 2017; Feng & Jones 2018), incorporando un tratamiento probabilístico riguroso de las incertidumbres.
- La metodología propuesta es compatible con el marco desarrollado por Bailer-Jones (2018) para estudiar encuentros estelares pasados con el Sol, adaptándolo al problema inverso de rastrear objetos interestelares hacia sus posibles fuentes.

## 7. Limitaciones, Preguntas Abiertas y Trabajo Futuro
**Limitaciones identificadas en el estudio:**
- **Completitud del catálogo estelar:** El conjunto AstroRV, aunque extenso, no incluye todas las estrellas cercanas con astrometría y velocidades radiales de alta precisión; futuras liberaciones de Gaia ampliarán significativamente este conjunto.
- **Modelado simplificado de eyección:** La distribución de velocidades de eyección se estima mediante un modelo semi-analítico que asume dispersión por un único planeta gigante; sistemas multi-planetarios, binarios estelares, o mecanismos alternativos (ej. inestabilidades dinámicas, encuentros estelares en cúmulos) no están explícitamente modelados.
- **Potencial galáctico axisimétrico:** El modelo de potencial omite componentes no axisimétricos (brazos espirales, barra galáctica) que podrían introducir desviaciones en trayectorias a escalas de tiempo >10 Myr.
- **Suposición de isotropía:** La estimación de Ppos asume que la densidad de trayectorias estelares es isotrópica en el volumen de encuentro; anisotropías en la distribución de velocidades estelares o en la geometría de eyección podrían modificar esta estimación.

**Preguntas abiertas:**
- ¿Cómo varían las IOP calculadas cuando se incorporan distribuciones de eyección más realistas, incluyendo dependencia con la arquitectura planetaria, masa estelar, y edad del sistema?
- ¿Qué fracción de los candidatos identificados posee evidencia observacional de planetas, discos de escombros, o binariedad que pueda validar físicamente su capacidad de eyección?
- ¿Cómo se modifican las IOP cuando se consideran encuentros estelares múltiples (ej. el objeto fue dispersado secuencialmente por más de un sistema estelar durante su tránsito interestelar)?
- ¿Qué impacto tiene la inclusión de potenciales galácticos no axisimétricos o de encuentros estelares cercanos en la precisión de las trayectorias retropropagadas a escalas de tiempo >10 Myr?

**Trabajo futuro sugerido:**
- **Actualización con Gaia DR3/DR4:** Re-ejecutar los cálculos con catálogos estelares ampliados y con menores incertidumbres en paralajes, movimientos propios y velocidades radiales.
- **Incorporación de modelos de eyección detallados:** Acoplar simulaciones N-cuerpos de sistemas planetarios para generar distribuciones de velocidad de eyección más realistas y dependientes de parámetros estelares/planetarios.
- **Extensión a múltiples objetos interestelares:** Aplicar la metodología de manera sistemática a futuros ISOs detectados por LSST/Rubin, permitiendo estudios estadísticos de poblaciones de progenitores.
- **Validación observacional:** Realizar seguimientos espectroscópicos y de alta resolución astrométrica de los candidatos principales para refinar sus parámetros y buscar signos de actividad planetaria o de eyección reciente.
- **Desarrollo de métricas de priorización:** Definir criterios adicionales (ej. presencia de planetas confirmados, edad estelar, metalicidad) para priorizar candidatos para observaciones de seguimiento.

## 8. Conclusión General de la Revisión
El artículo de Zuluaga et al. (2018) presenta una metodología general y cuantitativa para evaluar el origen interestelar de objetos menores detectados en el Sistema Solar, aplicada al caso de 1I/'Oumuamua. El estudio establece un marco probabilístico que incorpora explícitamente las incertidumbres en los elementos orbitales del objeto y en los parámetros astrométricos de las estrellas cercanas, mediante la generación de ensembles de trayectorias sustitutas y el cálculo de densidades numéricas mediante kernels de suavizado.

La aplicación al caso de 'Oumuamua identifica 16 estrellas candidatas como progenitores potenciales, con HIP 103749 (HD 200325) presentando la probabilidad de origen más alta bajo los supuestos del modelo. Los resultados se presentan de manera que pueden ser actualizados conforme mejore la información observacional, y el paquete computacional iWander se pone a disposición pública para facilitar la reproducibilidad y extensión del trabajo.

El artículo contribuye al campo de la dinámica interestelar al proporcionar una herramienta estructurada para transformar la pregunta cualitativa "¿de dónde viene este objeto?" en una evaluación cuantitativa de probabilidades relativa a un conjunto de estrellas candidatas. Si bien el estudio reconoce limitaciones en el modelado de mecanismos de eyección y en la completitud de los catálogos estelares, establece una base metodológica sólida que puede ser refinada con futuros datos astrométricos y modelos dinámicos más detallados. En conjunto, el trabajo representa un paso importante hacia la caracterización sistemática de los orígenes de objetos interestelares en la era de los sondeos de próxima generación.
