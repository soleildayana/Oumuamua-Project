
# Revisión: *Plausible home stars of the interstellar object ‘Oumuamua found in Gaia DR2*

## 1. Información Bibliográfica
- **Título:** Plausible home stars of the interstellar object ‘Oumuamua found in Gaia DR2
- **Autores:** Coryn A.L. Bailer-Jones, Davide Farnocchia, Karen J. Meech, Ramon Brasser, Marco Micheli, Sukanya Chakrabarti, Marc W. Buie, Olivier R. Hainaut
- **Afiliaciones principales:** Max Planck Institute for Astronomy (Alemania), Jet Propulsion Laboratory/Caltech (EE. UU.), Institute for Astronomy, Univ. of Hawai‘i (EE. UU.), Earth Life Science Institute (Japón), ESA SSA-NEO Coordination Centre (Italia), Rochester Institute of Technology (EE. UU.), Southwest Research Institute (EE. UU.), European Southern Observatory (Alemania)
- **Publicación:** *The Astronomical Journal* (versión draft: 25 de septiembre de 2018; publicado formalmente en 2018, Vol. 156, 205)
- **Identificador:** arXiv:1809.09009v1 [astro-ph.EP]

## 2. Contexto y Objetivo del Estudio
El descubrimiento de 1I/2017 U1 (‘Oumuamua) en octubre de 2017 marcó un hito al confirmar la existencia de objetos interestelares (ISOs) que transitan por el Sistema Solar. Dado que su trayectoria hiperbólica y su velocidad asintótica indican un origen externo al Sol, se asume que fue expulsado de un sistema planetario natal durante la fase de formación o migración planetaria. Estudios previos intentaron retrotraer su órbita bajo supuestos puramente gravitacionales y con catálogos estelares limitados (TGAS, Hipparcos), sin lograr candidatos convincentes.

El **objetivo específico** de este trabajo es identificar posibles estrellas de origen ("home stars") de ‘Oumuamua mediante el rastreo preciso de su trayectoria de entrada hacia el Sol, incorporando por primera vez:
1. Modelos no keplerianos que incluyen la aceleración no gravitacional detectada (atribuida a desgasificación tipo cometaria).
2. El catálogo **Gaia DR2**, que proporciona información de fase 6D (posición, paralaje, movimiento propio y velocidad radial) para ~7 millones de estrellas.
El estudio no busca validar teorías generales de formación planetaria, sino evaluar rigurosamente la viabilidad dinámica de encuentros estelares pasados que puedan explicar el origen del objeto bajo restricciones observacionales actuales.

## 3. Metodología y Enfoque
- **Tipo de estudio:** Análisis observacional combinado con integración numérica de órbitas en un potencial galáctico suave, complementado con tratamiento estadístico de incertidumbres.
- **Datos y fuentes:**
  - *‘Oumuamua:* Soluciones orbitales de Micheli et al. (2018) que incluyen 6 modelos de aceleración no gravitacional radial ($\propto r^{-2}$), derivados de astrometría terrestre y del HST.
  - *Estrellas:* Gaia Data Release 2 (7.2 millones de fuentes con astrometría y RVs). Se aplican filtros de calidad (paralaje positivo, `visibility_periods_used` ≥ 8, `unit_weight_error` < 35), reduciendo la muestra a 7.039.430 estrellas.
  - *Suplemento:* Búsqueda en SIMBAD de velocidades radiales no incluidas en Gaia DR2 (222.275 estrellas adicionales), integradas mediante el mismo procedimiento.
- **Procedimiento analítico:**
  1. **Aproximación de Movimiento Lineal (LMA):** Cálculo analítico rápido de parámetros de encuentro ($t_{enc}^{lma}, d_{enc}^{lma}, v_{enc}^{lma}$) para preseleccionar candidatas dentro de 10 pc en el pasado.
  2. **Integración orbital:** Propagación hacia atrás en el tiempo usando un potencial galáctico axisimétrico de tres componentes (disco, bulbo, halo), idéntico al usado en Bailer-Jones (2015).
  3. **Cuantificación de incertidumbres:** Muestreo de Monte Carlo mediante 2000 "sustitutos" (surrogates) por estrella, generados a partir de las covarianzas gaussianas 6D de Gaia y de los parámetros asintóticos de ‘Oumuamua. Se extraen medianas e intervalos de confianza al 90%.
  4. **Criterio de selección:** Estrellas con $d_{enc}^{med} < 2$ pc y velocidades relativas compatibles con mecanismos de eyección planetaria o estelar.

## 4. Marco Teórico y Formalismo Matemático Clave
El artículo se sustenta en varios pilares formales:
- **Vector asintótico de entrada:** Se calcula integrando la trayectoria hasta ~28.000 au y extrapolando keplerianamente. En el marco ICRF:
  $$\vec{v}_{\infty} = -v_{\infty} \begin{pmatrix} \cos\alpha \cos\delta \\ \sin\alpha \cos\delta \\ \sin\delta \end{pmatrix}$$
  donde $(\alpha, \delta)$ son la ascensión recta y declinación de la asíntota, y $v_{\infty}$ la velocidad asintótica baricéntrica.
- **Potencial Galáctico:** Modelo suave y estacionario que omite brazos espirales y la barra central, válido para escalas de tiempo < 5 Myr y distancias < 100 pc, donde las perturbaciones diferenciales son dominantes sobre las absolutas.
- **Mecanismos de eyección:**
  - *Dispersión por planeta gigante:* El cambio típico de energía específica por paso al periastro es $\|\Delta E\| \approx 10 (a_p/m_p/M_*)$ au$^{-1}$. La velocidad de escape resultante escala como $v_{esc} \propto \sqrt{m_p/a_p}$. Para alcanzar $v \gtrsim 10-25$ km/s se requiere un encuentro profundo y raro, o un sistema binario estelar.
  - *Encuentro estelar cercano (aproximación de impulso):* $\Delta V = 2GM_*/(v_* b)$. Demuestra que la eyección por paso de una estrella de campo es altamente improbable salvo parámetros de impacto extremadamente pequeños.
- **Tratamiento estadístico:** Distribuciones marginales de $t_{enc}, d_{enc}, v_{enc}$ derivadas de los 2000 sustitutos. La fuerte correlación negativa entre $t_{enc}$ y $v_{enc}$ refleja la componente radial del movimiento relativo.

## 5. Resultados Principales
De la muestra inicial, 28 estrellas (solo Gaia) y 13 (con RVs de SIMBAD) presentan $d_{enc}^{med} < 2$ pc. El estudio destaca **cuatro candidatos principales**:
1. **HIP 3757 (enana M2.5):** Encuentro más cercano. $t_{enc} = -0.99 \pm 0.03$ Myr, $d_{enc} = 0.60$ pc (IC 90%: 0.53–0.67 pc), $v_{enc} = 24.7$ km/s (IC 90%: 24.1–25.2 km/s).
2. **HD 292249 (enana G5):** Encuentro más lento dentro de 2 pc. $t_{enc} = -3.76$ Myr, $d_{enc} = 1.60$ pc, $v_{enc} = 10.7$ km/s.
3. **home-3 (probable enana K):** Compromiso distancia-velocidad. $t_{enc} = -6.30$ Myr, $d_{enc} = 1.01$ pc, $v_{enc} = 14.4$ km/s.
4. **home-4 (enana M5):** $t_{enc} = -1.14$ Myr, $d_{enc} = 0.88$ pc, $v_{enc} = 17.9$ km/s.

**Hallazgos adicionales:**
- Ninguno de los cuatro candidatos posee exoplanetas confirmados ni se conoce que sean sistemas binarios.
- Los parámetros de encuentro son robustos frente a los 6 modelos no gravitacionales probados; la dispersión asintótica de ‘Oumuamua es menor que las incertidumbres astrométricas estelares.
- Se predicen encuentros futuros: en ~0.72 Myr pasará a 0.33 pc de TYC 4600-1769-1 ($v_{rel} \approx 112$ km/s) y en ~29.000 años pasará a 0.46 pc de Ross 248.

## 6. Discusión y Análisis Crítico
El artículo logra un avance metodológico significativo respecto a búsquedas anteriores (Dybczyński & Królikowska 2018; Feng & Jones 2018; Portegies Zwart et al. 2018). La inclusión de la aceleración no gravitacional corrige la dirección asintótica en ~0.4°, lo que altera las distancias de encuentro en ~0.35 pc tras 50 pc de recorrido, invalidando candidatos previos basados en soluciones puramente gravitacionales.

**Puntos fuertes:**
- El uso de Gaia DR2 multiplica por ~20 el volumen de búsqueda 6D respecto a TGAS.
- El enfoque estadístico (surrogates + IC 90%) cuantifica rigurosamente la propagación de errores, evitando afirmaciones deterministas infundadas.
- La discusión sobre mecanismos de eyección es físicamente consistente: reconoce que $v_{enc} \gtrsim 10-25$ km/s es difícil de lograr con dispersión por un solo planeta gigante, favoreciendo sistemas binarios o eyecciones por inestabilidad dinámica múltiple.

**Crítica constructiva:**
- La correlación alta entre tiempo y velocidad de encuentro sugiere que pequeñas variaciones en $v_{\infty}$ desplazan significativamente $t_{enc}$. Aunque los autores lo reconocen, no exploran sistemáticamente cómo cambios en la modelización de la aceleración no gravitacional (asimétrica pre/perihelio) afectarían la jerarquía de candidatos.
- La suposición de que la aceleración no gravitacional es simétrica en la rama de entrada es necesaria pero no verificable. Si la desgasificación comenzó tardíamente por retraso térmico, la velocidad asintótica real podría diferir, alterando $d_{enc}$ y $v_{enc}$.
- El criterio de $d_{enc} < 2$ pc es arbitrario pero justificado por incertidumbres del potencial. Sin embargo, el artículo reconoce que encontrar encuentros cercanos es estadísticamente inevitable (~20 estrellas/Myr dentro de 1 pc del Sol), por lo que la baja velocidad relativa se convierte en el filtro crítico. Esto reduce la probabilidad de que HIP 3757 sea el origen real, dado su $v_{enc} \approx 25$ km/s.

## 7. Limitaciones, Preguntas Abiertas y Trabajo Futuro
**Limitaciones identificadas:**
- **Muestra restringida:** Solo 7 millones de estrellas tienen datos 6D en DR2. Dentro de 500 pc hay ~35 millones; la probabilidad a priori de capturar la estrella natal es baja.
- **Potencial galáctico simplificado:** La omisión de la barra, brazos espirales y encuentros N-cuerpo limita la precisión para retrotracciones > 5-10 Myr.
- **Efectos N-cuerpo:** Aunque se argumenta que son despreciables para encuentros recientes (< 1 Myr), son relevantes si ‘Oumuamua fue expulsado a baja velocidad hace > 10 Myr, ya que la estrella natal habría recorrido distancias comparables a la escala de correlación estelar local.
- **Falta de datos binarios/exoplanetarios:** Ningún candidato tiene confirmación de compañeras o planetas, lo que dificulta validar el mecanismo de eyección.

**Preguntas abiertas:**
- ¿Fue ‘Oumuamua expulsado por un planeta gigante, un sistema binario estelar, o por inestabilidad dinámica en un cúmulo estelar joven?
- ¿La aceleración no gravitacional observada corresponde a desgasificación de H₂O, H₂ radiolítico, u otro mecanismo? Esto afecta la reconstrucción de la órbita inbound.
- ¿Existen estrellas candidatas fuera de Gaia DR2 (enanas muy tenues, binarias resueltas incorrectamente) que coincidan mejor en distancia y velocidad?

**Trabajo futuro sugerido:**
- Integrar los datos de **Gaia DR3/DR4**, que ampliarán las RVs en un orden de magnitud y mejorarán la precisión astrométrica.
- Implementar potenciales galácticos con componentes no axisimétricos y simulaciones de N-cuerpo locales para escalas > 5 Myr.
- Combinar búsquedas dinámicas con estudios espectroscópicos de los candidatos para detectar binariedad o firmas de acreción/actividad planetaria.
- Esperar nuevos ISOs (ej. con el LSST/Rubin Observatory) para construir una distribución estadística de orígenes y validar modelos de eyección.

## 8. Conclusión General de la Revisión
El artículo de Bailer-Jones et al. representa un estudio riguroso, metodológicamente sólido y bien contextualizado dentro de la dinámica galáctica moderna. Logra su objetivo principal al identificar cuatro candidatos plausibles con parámetros de encuentro cuantificados estadísticamente, y demuestra de manera convincente por qué los estudios previos fallaron (falta de datos 6D precisos y uso de trayectorias puramente gravitacionales). 

Sin embargo, el estudio también revela una limitación intrínseca al problema: la inevitabilidad estadística de encuentros cercanos y la degeneración dinámica impiden señalar un origen definitivo con los datos actuales. La conclusión más valiosa del trabajo es que **la baja velocidad relativa de encuentro es un criterio más discriminante que la distancia mínima**, y que sin información complementaria (binariedad, discos, planetas) la atribución a un sistema específico seguirá siendo especulativa. 

En conjunto, el artículo establece el marco de referencia para futuras investigaciones de trazabilidad de ISOs, combina adecuadamente astrometría de alta precisión con dinámica galáctica, y sienta las bases para aprovechar las siguientes liberaciones de Gaia y los sondeos de próxima generación. Es una contribución fundamental al campo de la arqueología dinámica interestelar.
