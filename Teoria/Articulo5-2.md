# Revisión: *1I/'Oumuamua as an N₂ Ice Fragment of an Exo-Pluto Surface II: Generation of N₂ Ice Fragments and the Origin of 'Oumuamua*

## 1. Información Bibliográfica
- **Título:** 1I/'Oumuamua as an N₂ Ice Fragment of an Exo-Pluto Surface II: Generation of N₂ Ice Fragments and the Origin of 'Oumuamua
- **Autores:** Steven J. Desch, Alan P. Jackson
- **Afiliación:** School of Earth and Space Exploration, Arizona State University, Tempe, AZ, USA
- **Publicación:** *Journal of Geophysical Research: Planets*, Vol. 126, e2020JE006807 (2021)
- **DOI:** https://doi.org/10.1029/2020JE006807
- **Fechas:** Recibido 15 diciembre 2020 / Aceptado 11 marzo 2021 / Publicado en línea 2021
- **Tipo de documento:** Artículo de investigación (Parte II de un estudio en dos partes)
- **Artículo compañero:** Jackson & Desch (2021), https://doi.org/10.1029/2020JE006706
- **Repositorio de código/datos:** https://doi.org/10.5281/zenodo.4558478

## 2. Contexto y Objetivo del Estudio
El descubrimiento de 1I/'Oumuamua en octubre de 2017 por el telescopio Pan-STARRS marcó la primera detección confirmada de un objeto interestelar (ISO) en el Sistema Solar. En la Parte I de este estudio (Jackson & Desch, 2021), los autores demostraron que un cuerpo compuesto predominantemente de hielo de N₂ con dimensiones ~45 m × 44 m × 7.5 m y albedo ~0.64 puede satisfacer simultáneamente las restricciones observacionales sobre aceleración no gravitacional, tamaño, albedo, y ausencia de emisión detectable de CO, CO₂ o polvo.

El **objetivo específico** de esta Parte II es evaluar cuantitativamente si la dinámica del Cinturón de Kuiper primordial en nuestro Sistema Solar, específicamente durante la inestabilidad asociada con la migración de Neptuno, puede generar y eyectar un número suficiente de fragmentos de hielo de N₂ de tamaño similar a 'Oumuamua para explicar la densidad numérica inferida de objetos interestelares. El estudio busca:
1. Calcular la masa total de fragmentos superficiales generados por colisiones durante la inestabilidad dinámica que agotó el Cinturón de Kuiper.
2. Estimar la fracción de estos fragmentos compuesta de hielo de N₂ versus hielo de H₂O, basándose en la estructura diferenciada de cuerpos tipo Pluto.
3. Determinar la eficiencia de eyección de estos fragmentos hacia el espacio interestelar versus su captura en la Nube de Oort.
4. Comparar las predicciones del modelo con las densidades numéricas inferidas para ISOs tipo 'Oumuamua y con las propiedades observadas del cometa interestelar 2I/Borisov.
5. Evaluar la viabilidad de que fragmentos de N₂ sobrevivan a la erosión por rayos cósmicos galácticos durante su tránsito por el medio interestelar.

## 3. Metodología y Enfoque
- **Tipo de estudio:** Modelado analítico-numérico acoplado a estimaciones de dinámica orbital, colisiones planetesimales, y evolución termofísica en el medio interestelar.
- **Datos y fuentes:**
  - *Propiedades del Cinturón de Kuiper:* Distribuciones de frecuencia de tamaños (SFD) de KBOs de Fraser et al. (2014) y Singer et al. (2019); masas y radios de cuerpos tipo Pluto y Gonggong de Nesvorný & Vokrouhlický (2016); densidad actual del Cinturón de Kuiper de Pitjeva & Pitjev (2018).
  - *Propiedades de eyección:* Eficiencias de captura en la Nube de Oort de Dones et al. (2004, 2015), Brasser & Morbidelli (2013), y Vokrouhlický et al. (2019); tiempos de eyección por Júpiter de Wyatt et al. (2017).
  - *Propiedades de erosión interestelar:* Tasas de sublimación térmica, fotodesorción, abrasión por polvo, y erosión por rayos cósmicos galácticos (GCR) calculadas en la Parte I y basadas en datos experimentales de Vasconcelos et al. (2017) y Webber (1998).
  - *Historia de formación estelar:* Tasa de formación estelar en la vecindad solar de Mor et al. (2019) para modelar la variación temporal del flujo de GCR.
- **Procedimiento analítico:**
  1. **Estimación de masa colisional:** Cálculo de la masa total de material eyectado de las superficies de ~2,000 cuerpos tipo Pluto (R ~ 1,200 km) y ~6,000 cuerpos tipo Gonggong (R ~ 600 km) durante la inestabilidad dinámica, usando relaciones de escalado de cráteres de Housen & Holsapple (2011) y probabilidades de colisión basadas en densidades numéricas y secciones transversales.
  2. **Composición de fragmentos:** Estimación de la fracción de masa eyectada compuesta de N₂ versus H₂O, basada en espesores de capas de N₂ inferidos de inventarios de nitrógeno cósmico (Lodders, 2003) y modelos de evolución geoquímica de KBOs diferenciados (McKinnon et al., 2020; Robuchon & Nimmo, 2011).
  3. **Distribución de tamaños de fragmentos:** Suposición de una distribución diferencial de tamaños con pendiente q ≈ 5–6 para fragmentos colisionales, basada en estudios de cráteres secundarios en Marte (Robbins & Hynek, 2011), con un diámetro mínimo D_min ~ 50 m para supervivencia interestelar.
  4. **Eficiencia de eyección:** Combinación de probabilidades de supervivencia contra sublimación térmica durante pasos por 5 au, colisiones con otros KBOs durante la fase de eyección (~50 Myr), y captura versus eyección por Júpiter, para estimar la fracción de fragmentos que alcanzan el espacio interestelar.
  5. **Erosión interestelar:** Cálculo de tasas de erosión por GCR (~6.6 m/Gyr en la vecindad solar actual) y corrección por variaciones históricas en el flujo de GCR debido a paso por brazos espirales y evolución de la tasa de formación estelar galáctica.
  6. **Extrapolación galáctica:** Multiplicación del número de objetos eyectados por el Sistema Solar por una densidad estelar promedio de 0.12 M⊙ pc⁻³ (Widmark & Monari, 2019) para estimar densidades numéricas en el medio interestelar, asumiendo que la eficiencia de eyección por masa estelar es típica entre sistemas estelares.

## 4. Marco Teórico y Formalismo Matemático Clave
El artículo emplea los siguientes elementos formales:
- **Relaciones de escalado de eyección por impacto:** La masa de material eyectado de un cuerpo helado por un impactor de masa M_imp y velocidad de impacto V_imp se modela como:
  $$M_{\text{ejecta}} = M_{\text{imp}} C \left(\frac{V_{\text{esc}}}{V_{\text{imp}} \sin\theta}\right)^{-3\mu}$$
  donde μ = 0.55, C = 0.14, V_esc es la velocidad de escape del cuerpo objetivo, y θ es el ángulo de impacto respecto a la normal (Housen & Holsapple, 2011; Hyodo & Genda, 2020).
- **Probabilidad de colisión:** Para un cuerpo con sección transversal σ moviéndose a velocidad relativa V_rel a través de un campo de objetivos con densidad numérica n durante un tiempo t:
  $$P_{\text{coll}} = 1 - \exp\left[-n \sigma V_{\text{rel}} t\right]$$
- **Distribución de frecuencias de tamaños (SFD):** Para fragmentos colisionales, se asume una distribución diferencial dN/dD ∝ D⁻q con q ≈ 5–6, lo que implica que el valor promedio de D³ es:
  $$\langle D^3 \rangle = \frac{q-1}{q-4} D_{\text{min}}^3$$
  Para q = 6 y D_min = 50 m, esto da ⟨D³⟩ ≈ 2.5 D_min³.
- **Erosión por rayos cósmicos galácticos:** Basado en experimentos de irradiación de hielos N₂:CH₄ con iones de oxígeno (Vasconcelos et al., 2017), se infiere una tasa de remoción de ~1 molécula de N₂ por cada ~26 eV depositados, resultando en una tasa de erosión de:
  $$\dot{R}_{\text{GCR}} \approx 6.6 \text{ m/Gyr} \times \left(\frac{F_{\text{GCR}}}{F_{\text{GCR,☉}}}\right)$$
  donde F_GCR es el flujo de GCR local, que varía con la posición galáctica y la historia de formación estelar.
- **Densidad numérica interestelar:** La densidad de fragmentos en el ISM se estima como:
  $$n_{\text{ISM}} = \left(\frac{N_{\text{ejected}}}{M_{\star,\text{ejected}}}\right) \times \rho_{\star,\text{avg}} \times f_{\text{survival}}$$
  donde ρ_⋆,avg ≈ 0.12 M⊙ pc⁻³ es la densidad estelar promedio y f_survival es la fracción de fragmentos que sobreviven a la erosión interestelar hasta el presente.

## 5. Resultados Principales
1. **Masa total de fragmentos generados:** Durante la inestabilidad dinámica que agotó el Cinturón de Kuiper (~50 Myr de duración), se estima que colisiones entre KBOs pequeños y cuerpos tipo Pluto/Gonggong generaron ~0.074 M⊕ de fragmentos superficiales, equivalentes a una erosión global de ~4 km en Plutos y ~11 km en Gonggongs.
2. **Composición de fragmentos:** Asumiendo que las capas superficiales de Plutos y Gonggongs contienen ~35 km y ~18 km de hielo de N₂ puro, respectivamente, se calcula que ~60% de la masa eyectada (~0.043 M⊕) corresponde a fragmentos de N₂, con el resto siendo principalmente hielo de H₂O.
3. **Número y tamaño de fragmentos:** Con una distribución de tamaños q ≈ 6 y D_min = 50 m, la masa total de fragmentos implica ~2.7 × 10¹⁵ fragmentos con D > 50 m en el Sistema Solar temprano, con un diámetro típico ~70 m y masa promedio ~1.6 × 10⁸ kg, consistente con la masa inicial estimada para 'Oumuamua en la Parte I.
4. **Eficiencia de eyección:** Combinando supervivencia contra sublimación (~94%), colisiones durante eyección (~61% de pérdida), y eficiencia de eyección por Júpiter (~80%), se estima que ~29% de los fragmentos de H₂O y ~18% de los de N₂ alcanzan el espacio interestelar, resultando en ~5.6 × 10¹⁴ fragmentos eyectados, mitad N₂ y mitad H₂O.
5. **Densidades interestelares predichas:** Extrapolar a la Galaxia asumiendo eyección típica por masa estelar produce densidades numéricas en el ISM de:
   - Fragmentos de N₂: ~1.4 × 10¹² pc⁻³
   - Fragmentos de H₂O: ~1.1 × 10¹³ pc⁻³
   - Cometas/KBOs con D > 1 km: ~6.4 × 10¹⁰ pc⁻³
   - Total de objetos con D > 50 m: ~1.4 × 10¹³ pc⁻³
   Estos valores son consistentes con el rango inferido por Portegies Zwart et al. (2018): 3.5 × 10¹³ – 2 × 10¹⁵ pc⁻³.
6. **Supervivencia y edades medias:** La erosión por GCR reduce la población de fragmentos pequeños con el tiempo. Se estima que:
   - Fragmentos de N₂ sobreviven típicamente ~1 Gyr, con edad media ~0.5 Gyr
   - Fragmentos de H₂O sobreviven ~3 Gyr, con edad media ~2 Gyr
   - Cometas/KBOs grandes sobreviven indefinidamente, con edad media ~5 Gyr
7. **Comparación con 2I/Borisov:** La diferencia en velocidades respecto al LSR entre 'Oumuamua (~9 km s⁻¹) y Borisov (~35 km s⁻¹) es consistente con sus edades inferidas: 'Oumuamua, como fragmento de N₂ joven, no ha tenido tiempo de adquirir alta dispersión de velocidad, mientras que Borisov, como cometa antiguo, sí.
8. **Posibles análogos en la Nube de Oort:** Se estima que ~0.07% de los cometas de período largo con D > 1 km en la Nube de Oort podrían ser fragmentos de N₂ sobrevivientes. El cometa C/2016 R2, con química inusual (alta producción de N₂ y CO, baja producción de H₂O y polvo), se señala como un candidato plausible.

## 6. Discusión y Análisis Descriptivo
El artículo integra de manera coherente la dinámica del Sistema Solar temprano, la geoquímica de cuerpos diferenciados del Cinturón de Kuiper, y la evolución interestelar de fragmentos pequeños para proponer un escenario completo para el origen de 'Oumuamua. El enfoque metodológico se caracteriza por tratar explícitamente cada etapa del proceso: generación colisional, composición superficial, eyección dinámica, y erosión interestelar.

**Aspectos metodológicos destacados:**
- La estimación de la masa eyectada por colisiones utiliza relaciones de escalado validadas experimentalmente y considera tanto la distribución de tamaños de impactores como la geometría de excavación de cráteres para estimar la profundidad de material removido.
- La distinción entre fragmentos de N₂ y H₂O se basa en un modelo estratificado de la corteza de KBOs diferenciados, con capas de N₂ superficiales sobre un sustrato de H₂O, consistente con observaciones de Pluto y Tritón.
- El tratamiento de la erosión por GCR incorpora no solo la tasa local actual, sino también variaciones históricas debido a paso por brazos espirales y evolución de la formación estelar galáctica, proporcionando estimaciones más realistas de supervivencia a largo plazo.
- La comparación con observaciones de 'Oumuamua y Borisov se realiza mediante métricas cuantitativas (densidades numéricas, edades medias, dispersiones de velocidad) en lugar de afirmaciones cualitativas.

**Relación con observaciones:**
- La densidad numérica predicha de fragmentos pequeños (~1.4 × 10¹³ pc⁻³) cae dentro del rango inferido estadísticamente a partir de la detección de 'Oumuamua, validando la viabilidad del mecanismo propuesto.
- La proporción predicha de fragmentos de N₂ entre objetos pequeños detectables (~10–50%, dependiendo de correcciones por albedo) es consistente con que el primer ISO pequeño detectado sea de esta composición.
- La diferencia en edades medias entre fragmentos de N₂ (~0.5 Gyr) y cometas tradicionales (~5 Gyr) explica naturalmente la diferencia en velocidades respecto al LSR entre 'Oumuamua y Borisov.
- La predicción de que ~0.1% de los cometas de período largo podrían ser fragmentos de N₂ es consistente con la posible identificación de C/2016 R2 como tal objeto.

**Contexto en la literatura:**
- El estudio complementa la Parte I al demostrar que no solo es físicamente posible que 'Oumuamua sea un fragmento de N₂, sino que también es estadísticamente plausible que tales fragmentos sean eyectados en números suficientes para explicar las observaciones.
- El escenario propuesto contrasta con hipótesis que invocan composiciones exóticas (H₂ puro, agregados fractales) al basarse en materiales y procesos observados en el Sistema Solar.
- La universalidad postulada de inestabilidades dinámicas tipo "Nice model" se alinea con evidencia creciente de que tales eventos son comunes en sistemas exoplanetarios (Raymond et al., 2010, 2011, 2012).

## 7. Limitaciones, Preguntas Abiertas y Trabajo Futuro
**Limitaciones identificadas en el estudio:**
- **Suposición de eyección típica:** El modelo asume que la eficiencia de eyección por masa estelar es similar entre sistemas estelares, pero no cuantifica explícitamente cómo variaciones en arquitectura planetaria, masa estelar, o entorno de cúmulo podrían alterar esta eficiencia.
- **Incertidumbre en distribuciones de tamaños:** La pendiente q ≈ 6 para fragmentos colisionales se basa en extrapolaciones de estudios de cráteres secundarios en Marte; valores diferentes alterarían significativamente el número de fragmentos pequeños predichos.
- **Propiedades de erosión por GCR:** La tasa de erosión se infiere de experimentos con iones de oxígeno a energías específicas; la extrapolación al espectro completo de GCR introduce incertidumbre en la tasa real de remoción de N₂.
- **Estructura de KBOs exóticos:** El modelo asume que "exo-Plutos" tienen estructuras y composiciones superficiales similares a Pluto y Tritón; variaciones en historia térmica, composición inicial, o evolución geoquímica podrían alterar la fracción de N₂ eyectado.

**Preguntas abiertas:**
- ¿Cuál es la distribución real de arquitecturas planetarias y eficiencias de eyección entre sistemas estelares de diferentes masas y edades?
- ¿Cómo varía la composición superficial de KBOs diferenciados con la metalicidad estelar, distancia orbital, o historia de irradiación?
- ¿Qué fracción de fragmentos eyectados mantiene formas elongadas estables durante su tránsito interestelar, y cómo afecta esto a su detectabilidad?
- ¿Pueden mecanismos alternativos de generación de ISOs (ej. eyección directa de planetesimales, disruptores tidales en sistemas binarios) contribuir significativamente a la población observada?

**Trabajo futuro sugerido:**
- **Simulaciones N-cuerpos de eyección:** Implementar integraciones dinámicas explícitas de la eyección de fragmentos durante inestabilidades tipo "Nice model" para cuantificar eficiencias de eyección en función de arquitectura planetaria.
- **Modelado geoquímico de exo-Plutos:** Desarrollar modelos de evolución térmica y química de KBOs en sistemas exoplanetarios para predecir variaciones en espesores de capas de N₂ y composiciones superficiales.
- **Experimentos de erosión interestelar:** Medir tasas de erosión de hielos astrofísicos bajo irradiación con espectros realistas de GCR y fotones UV para reducir incertidumbres en modelos de supervivencia.
- **Búsquedas observacionales de análogos:** Realizar estudios espectroscópicos de alta sensibilidad de cometas de período largo para identificar firmas de N₂ y otros volátiles hipervolátiles que podrían indicar origen como fragmentos superficiales.
- **Predicciones para LSST/Rubin:** Cuantificar tasas esperadas de detección de ISOs pequeños con diferentes composiciones y propiedades dinámicas para guiar estrategias de seguimiento con el Vera C. Rubin Observatory.

## 8. Conclusión General de la Revisión
El artículo de Desch & Jackson (2021, Parte II) presenta una evaluación cuantitativa y sistemática de la viabilidad dinámica y estadística del escenario propuesto en la Parte I: que 1I/'Oumuamua es un fragmento de hielo de N₂ eyectado de la superficie de un cuerpo tipo Pluto en otro sistema estelar. El estudio demuestra que la inestabilidad dinámica que agotó el Cinturón de Kuiper primordial en nuestro Sistema Solar puede generar ~0.074 M⊕ de fragmentos superficiales, de los cuales ~60% (~0.043 M⊕) corresponderían a hielo de N₂, y que una fracción significativa de estos fragmentos (~18% para N₂) puede ser eyectada hacia el espacio interestelar.

La extrapolación de estos resultados a la Galaxia, asumiendo que la eficiencia de eyección por masa estelar es típica entre sistemas estelares, produce densidades numéricas de fragmentos pequeños en el medio interestelar (~1.4 × 10¹³ pc⁻³) que son consistentes con el rango inferido estadísticamente a partir de la detección de 'Oumuamua. Además, el modelo explica naturalmente las diferencias observadas entre 'Oumuamua y 2I/Borisov en términos de composición, edad, y dispersión de velocidad.

El trabajo establece predicciones observacionales concretas que pueden ser validadas con futuros sondeos: una población dominante de ISOs pequeños con D ~ 50–100 m, una fracción significativa (~10–50%) de los cuales deberían ser fragmentos de N₂ con albedos altos (~0.6–0.7) y aceleraciones no gravitacionales sin actividad cometaria detectable. En conjunto, el artículo contribuye al esfuerzo por comprender los mecanismos de generación, eyección, y evolución de objetos interestelares, y proporciona un marco cuantitativo para interpretar futuras detecciones con el LSST/Rubin Observatory y otras instalaciones de próxima generación.
