# Revisión: *1I/'Oumuamua as an N₂ Ice Fragment of an exo-Pluto Surface: I. Size and Compositional Constraints*

## 1. Información Bibliográfica
- **Título:** 1I/'Oumuamua as an N₂ Ice Fragment of an exo-Pluto Surface: I. Size and Compositional Constraints
- **Autores:** Alan P. Jackson, Steven J. Desch
- **Afiliación:** School of Earth and Space Exploration, Arizona State University, Tempe, AZ, USA
- **Publicación:** *Journal of Geophysical Research: Planets*, Vol. 126, e2020JE006706 (2021)
- **DOI:** https://doi.org/10.1029/2020JE006706
- **Fechas:** Recibido 22 septiembre 2020 / Aceptado 11 marzo 2021
- **Tipo de documento:** Artículo de investigación (Parte I de un estudio en dos partes)
- **Repositorio de código/datos:** https://doi.org/10.5281/zenodo.4558478

## 2. Contexto y Objetivo del Estudio
El descubrimiento de 1I/'Oumuamua en octubre de 2017 por el telescopio Pan-STARRS marcó la primera detección confirmada de un objeto interestelar (ISO) en el Sistema Solar. Este objeto presentó un conjunto de propiedades observacionales que incluyen: órbita hiperbólica (e = 1.2), variación extrema en la curva de luz (>2.5 mag), relación de ejes altamente elongada (5:1 a 10:1), espectro rojo sin características moleculares identificables, ausencia de coma de polvo o gas detectable en observaciones ópticas, infrarrojas y de radio, y una aceleración no gravitacional significativa con dependencia radial aproximadamente proporcional a r⁻².

El **objetivo específico** de este trabajo es evaluar cuantitativamente si un cuerpo compuesto predominantemente de hielo de N₂ puede satisfacer simultáneamente las restricciones observacionales disponibles sobre: (i) la magnitud y dependencia radial de la aceleración no gravitacional, (ii) el tamaño y albedo inferidos a partir de la fotometría y límites de emisión térmica, (iii) la ausencia de detección de especies volátiles como CO, CO₂ y polvo, y (iv) la evolución temporal de la forma y masa durante el paso por el Sistema Solar. El estudio se enmarca como la primera parte de un análisis en dos etapas, donde esta sección se concentra en las restricciones físicas y composicionales, mientras que la Parte II (Desch & Jackson, 2021) aborda la viabilidad dinámica de la generación y eyección de tales fragmentos.

## 3. Metodología y Enfoque
- **Tipo de estudio:** Modelado numérico acoplado a análisis termodinámico y dinámico, con comparación sistemática de múltiples composiciones de hielo.
- **Datos y fuentes:**
  - *Observacionales de 'Oumuamua:* Solución orbital de Micheli et al. (2018) con aceleración no gravitacional A₁ = (4.92 ± 0.16) × 10⁻⁶ m s⁻² a 1 au; parámetros de forma derivados por Mashchenko (2019) para soluciones prolata y oblata; límites superiores de producción de polvo, CO, CO₂ y CN de Trilling et al. (2018), Jewitt et al. (2017) y Park et al. (2018); albedos geométrico y de Bond de Pluto y Tritón de Buratti et al. (2015, 2017) y Hicks & Buratti (2004).
  - *Propiedades termofísicas de hielos:* Valores de entalpía de sublimación, densidad, capacidad calorífica, conductividad térmica y frecuencia vibracional de red para H₂, Ne, CH₄, CO, N₂, NH₃, O₂, CO₂ y H₂O, compilados de la literatura experimental (Tabla A1 del artículo).
- **Procedimiento analítico:**
  1. **Formulación del balance energético:** Se establece una ecuación de conservación de energía en la superficie que equilibra la radiación solar absorbida con la emisión térmica infrarroja, el enfriamiento evaporativo por sublimación y el transporte de calor hacia el interior del cuerpo (Ecuación 1).
  2. **Cálculo de la tasa de pérdida de masa:** Se deriva la velocidad de cambio del radio mediante una expresión de tipo Arrhenius que depende de la temperatura superficial y la entalpía de sublimación (Ecuación 2).
  3. **Conversión a aceleración no gravitacional:** La tasa de pérdida de masa se transforma en una fuerza dirigida anti-solar mediante un factor geométrico (1/3) que promedia la componente radial del momento del gas sublimado sobre la hemisfera iluminada, multiplicada por una velocidad efectiva de eyección calculada en el régimen de flujo fluido (Ecuaciones 4-6).
  4. **Exploración del espacio de parámetros:** Se evalúa la aceleración predicha como función del albedo común (p = pG = pB) para nueve composiciones de hielo puro, manteniendo las relaciones de ejes de la solución oblata de Mashchenko (2019) pero escalando las dimensiones con p⁻¹/².
  5. **Integración temporal:** Se propaga la evolución de masa, temperatura y relación de ejes hacia adelante y atrás en el tiempo a lo largo de la órbita hiperbólica, asumiendo pérdida isotrópica de masa y rotación caótica que promedia la iluminación.
  6. **Evaluación de erosión interestelar:** Se calculan tasas de erosión por sublimación térmica, fotodesorción, abrasión por polvo y rayos cósmicos galácticos (GCR) para estimar la supervivencia del cuerpo durante su tránsito por el medio interestelar (ISM).

## 4. Marco Teórico y Formalismo Matemático Clave
El artículo emplea los siguientes elementos formales:
- **Balance energético superficial:**
  $$\xi_0 \frac{L_\odot}{4\pi d^2}(1-p_B) = \epsilon\sigma T_{surf}^4 + n\left[\Delta H_{sub} + \Delta H_{trans} + mC_p(T_{surf}-T_{int})\right]\frac{dR}{dt}$$
  donde ξ₀ es la razón área proyectada/área total (0.25 para iluminación isotrópica), pB el albedo de Bond, ϵ la emisividad infrarroja (~0.85), n la densidad numérica de moléculas en el hielo, m la masa molecular, Cp la capacidad calorífica, y ΔHsub/trans las entalpías de sublimación y transición de fase.
- **Velocidad de recesión del radio:**
  $$\frac{dR}{dt} = -\frac{\nu}{n^{1/3}}\exp\left(-\frac{\Delta H_{sub}}{kT_{surf}}\right)$$
  con ν la frecuencia vibracional de red y k la constante de Boltzmann.
- **Aceleración no gravitacional:**
  $$a = \frac{\tau\xi_0 S}{3M}\sqrt{\frac{8kT_{surf}}{\pi m}}\left[\frac{L_\odot}{4\pi d^2}(1-p_B) - \epsilon\sigma T_{surf}^4 - n(\Delta H_{trans} + mC_p\Delta T)\frac{dR}{dt}\right]$$
  donde τ ≈ 0.45 es un factor de promedio de velocidad para flujos cometarios, S el área superficial y M la masa del cuerpo.
- **Escalado con albedo:** Las dimensiones lineales escalan como pG⁻¹/², la masa como pG⁻³/², y la relación masa/área como pG⁻¹/². La aceleración predicha escala aproximadamente como p¹/²(1-p), produciendo dos soluciones de albedo para una aceleración dada.
- **Erosión por GCR:** Se infiere una tasa de remoción de ~1 molécula de N₂ por cada ~26 eV depositados por rayos cósmicos, basada en experimentos de irradiación con iones de oxígeno, resultando en una tasa de erosión de ~6.6 m/Gyr en el entorno solar actual.

## 5. Resultados Principales
1. **Viabilidad composicional:** Entre los nueve hielos evaluados (H₂, Ne, CH₄, CO, N₂, NH₃, O₂, CO₂, H₂O), solo CH₄, CO y N₂ pueden proporcionar la aceleración no gravitacional observada para algún valor de albedo. CO está excluido por límites observacionales de producción, y CH₄ se observa típicamente como trazas disueltas en N₂ en cuerpos del Sistema Solar exterior. El N₂ emerge como la composición más plausible.
2. **Solución de albedo y dimensiones:** El N₂ reproduce la aceleración observada para dos valores de albedo: p ≈ 0.12 y p ≈ 0.64. La solución de alto albedo (0.64) coincide con los albedos geométrico y de Bond reportados para las superficies de N₂ de Pluto (pG = 0.62 ± 0.03, pB = 0.72 ± 0.07) y Tritón. Con p = 0.64, las dimensiones inferidas en el momento de las observaciones (d = 1.42 au) son: 45.5 m × 43.9 m × 7.5 m, con masa 8.0 × 10⁶ kg.
3. **Evolución durante el paso solar:** La pérdida de masa es dominada por el intervalo de ~50 días alrededor del perihelio (0.255 au), durante el cual la masa disminuye en un factor ~10 y la relación de ejes a/c aumenta de ~2:1 a ~6:1. El enfriamiento evaporativo mantiene la temperatura superficial por debajo de 47 K incluso en perihelio. La aceleración predicha sigue una dependencia ~d⁻¹.⁸, consistente con el ajuste observacional de Micheli et al. (2018).
4. **Compatibilidad con límites de actividad:** La tasa de producción de N₂ calculada (~8 × 10²⁴ moléculas s⁻¹ a 2 au) implica tasas de producción de CO y CO₂ disueltos (~0.1% y ~1% en peso, respectivamente, como en Pluto) que permanecen por debajo de los límites superiores de Spitzer. La pérdida de masa total (~0.37 kg s⁻¹) está muy por debajo del límite de producción de polvo (<9 kg s⁻¹).
5. **Erosión interestelar:** La sublimación térmica es negligible a temperaturas del ISM (~4.6 K). La fotodesorción y abrasión por polvo producen tasas de erosión <1 cm/Gyr. Los GCR dominan con ~6.6 m/Gyr en el entorno solar actual; considerando variaciones históricas en la tasa de formación estelar y paso por brazos espirales, la tasa promedio podría ser ~2-3 veces mayor. Un tiempo de tránsito de ~0.4-0.5 Gyr implicaría una erosión de ~10 m por semieje, consistente con una masa inicial ~2 × 10⁷ kg al momento de eyección.
6. **Rotación y torque:** El valor del parámetro de brazo de palanca efectivo ζ inferido para la solución de alto albedo (log ζ ≈ -2.74) permanece dentro del rango observado para cometas, y es consistente con sublimación distribuida sobre la hemisfera en lugar de chorros localizados.

## 6. Discusión y Análisis Descriptivo
El artículo presenta una evaluación sistemática de la hipótesis de que 'Oumuamua es un fragmento de hielo de N₂, integrando modelado termodinámico, dinámico y comparativo con observaciones del Sistema Solar. El enfoque metodológico se caracteriza por tratar el albedo como variable libre, lo que permite identificar dos soluciones físicamente posibles y seleccionar la más consistente con materiales conocidos.

**Aspectos metodológicos destacados:**
- La inclusión explícita del enfriamiento evaporativo en el balance energético evita sobreestimar temperaturas superficiales y tasas de sublimación, particularmente relevante para hielos volátiles cerca del perihelio.
- La suposición de pérdida isotrópica de masa, justificada por la rotación caótica y el promedio temporal, simplifica el cálculo sin introducir sesgos sistemáticos evidentes en la escala de integración.
- La comparación directa con propiedades observadas de Pluto y Tritón (albedo, fracciones de trazas de CO/CH₄ en N₂) proporciona un anclaje empírico para la plausibilidad composicional.
- La estimación de erosión por GCR se basa en datos experimentales de irradiación de hielos análogos, extrapolados con factores de escala físicos (energía depositada por molécula removida).

**Relación con observaciones:**
- La solución de alto albedo (p = 0.64) reconcilia el tamaño pequeño inferido con la detectabilidad por Pan-STARRS y los límites de emisión térmica de Spitzer.
- La evolución predicha de la relación de ejes (2:1 → 6:1) ofrece un mecanismo físico para la forma extremadamente elongada sin requerir condiciones iniciales inusuales.
- La compatibilidad con límites de producción de CO, CO₂ y polvo se logra mediante la suposición de impurezas trazas en proporciones similares a las observadas en superficies de Pluto, evitando la necesidad de mecanismos de supresión de actividad adicionales.

**Contexto en la literatura:**
- El estudio contrasta con propuestas que invocan composiciones exóticas (H₂ puro, agregados fractales de H₂O) al basarse en un material observado abundantemente en el Sistema Solar.
- La explicación de la aceleración no gravitacional mediante sublimación de N₂ evita inconsistencias teóricas asociadas con la estabilidad y formación de cuerpos de H₂ en condiciones interestelares.
- El marco propuesto es compatible con modelos de eyección dinámica tratados en la Parte II del estudio, estableciendo una conexión entre propiedades físicas observadas y procesos de formación planetaria.

## 7. Limitaciones, Preguntas Abiertas y Trabajo Futuro
**Limitaciones identificadas en el estudio:**
- **Suposición de isotropía:** La pérdida de masa isotrópica y la iluminación promedio (ξ₀ = 0.25) simplifican la geometría real; variaciones locales en la sublimación podrían alterar la evolución de la forma y el torque rotacional.
- **Propiedades termofísicas:** Los valores de conductividad térmica, capacidad calorífica y frecuencia vibracional para N₂ a bajas temperaturas tienen incertidumbres experimentales que podrían afectar las tasas calculadas de pérdida de masa y penetración térmica.
- **Historia térmica interestelar:** La temperatura interior inicial (Tint = 4.6 K) asume equilibrio con CMB y GCR; variaciones en el entorno interestelar (nubes moleculares, regiones de formación estelar) podrían modificar esta condición de frontera.
- **Composición de trazas:** Las fracciones de CO y CH₄ disueltos en N₂ se asumen por analogía con Pluto; composiciones diferentes en "exo-Plutos" podrían alterar las predicciones de actividad detectable.
- **Erosión por GCR:** La extrapolación de datos experimentales de irradiación con iones de oxígeno a todo el espectro de GCR introduce incertidumbre en la tasa de erosión a largo plazo.

**Preguntas abiertas:**
- ¿Cuál es la distribución real de albedos y composiciones superficiales en cuerpos tipo Pluto en otros sistemas estelares, y cómo se compara con las propiedades inferidas para 'Oumuamua?
- ¿Pueden mecanismos alternativos de aceleración no gravitacional (ej. presión de radiación en estructuras de baja densidad, eyección de polvo submicrométrico) reproducir las observaciones sin requerir sublimación de volátiles?
- ¿Cómo afecta la posible presencia de una costra procesada por irradiación interestelar a la eficiencia de sublimación y a la retención de volátiles subsuperficiales?
- ¿Qué fracción de los fragmentos eyectados de superficies de exo-Plutos sobreviviría la erosión interestelar para alcanzar el Sistema Solar con propiedades observables similares a 'Oumuamua?

**Trabajo futuro sugerido:**
- **Mediciones de laboratorio:** Determinación experimental de tasas de sublimación, conductividades térmicas y yields de fotodesorción para hielos de N₂ puros y con trazas de CO/CH₄ en condiciones relevantes para el ISM y el Sistema Solar interior.
- **Modelado termomecánico acoplado:** Simulaciones que incluyan la evolución de la porosidad, formación de costras por sinterización y retroalimentación entre sublimación y estructura interna para evaluar la robustez de la solución oblata.
- **Observaciones de seguimiento:** Búsqueda de aceleraciones no gravitacionales en cometas pequeños de período largo e interestelares descubiertos por el LSST/Rubin Observatory, con sensibilidad a líneas espectrales de N₂ en UV y a emisión de polvo grueso en mm/sub-mm.
- **Caracterización de análogos solares:** Estudios espectroscópicos de alta resolución de superficies de Pluto, Tritón y otros KBOs para cuantificar la variabilidad en fracciones de trazas, albedos y propiedades termofísicas, reduciendo degeneraciones en la inferencia composicional.
- **Integración con modelos de eyección:** Combinación de las restricciones físicas de esta Parte I con los cálculos dinámicos de la Parte II para predecir distribuciones de tamaños, albedos y tasas de detección de fragmentos de N₂ en sondeos futuros.

## 8. Conclusión General de la Revisión
El artículo de Jackson & Desch (2021, Parte I) presenta una evaluación cuantitativa y sistemática de la hipótesis de que 1I/'Oumuamua es un fragmento de hielo de N₂ proveniente de la superficie de un cuerpo tipo Pluto en otro sistema estelar. El estudio demuestra que un cuerpo compuesto predominantemente de N₂, con albedo ~0.64 y dimensiones ~45 m × 44 m × 7.5 m en el momento de las observaciones, puede satisfacer simultáneamente las restricciones observacionales sobre aceleración no gravitacional, tamaño, albedo, ausencia de actividad detectable de CO/CO₂/polvo, y evolución temporal de forma y masa.

La propuesta se fundamenta en propiedades termofísicas medidas experimentalmente para hielos astrofísicos y en analogías empíricas con superficies observadas en el Sistema Solar exterior. El mecanismo de sublimación de N₂ proporciona una explicación física coherente para la aceleración no gravitacional sin requerir composiciones exóticas no observadas, y la evolución predicha de la relación de ejes ofrece un camino natural hacia la forma altamente elongada inferida.

El trabajo establece predicciones observacionales concretas que pueden ser validadas con futuros sondeos: fragmentos interestelares de N₂ deberían exhibir aceleraciones no gravitacionales con dependencia ~d⁻², albedos altos (~0.6-0.7), y ausencia de emisión detectable de CO/CO₂/polvo a niveles compatibles con trazas disueltas. En conjunto, el artículo contribuye al esfuerzo por comprender la diversidad de composiciones y comportamientos dinámicos en cuerpos menores interestelares, y proporciona un marco cuantitativo para interpretar futuras detecciones con el LSST/Rubin Observatory y otras instalaciones de próxima generación.
