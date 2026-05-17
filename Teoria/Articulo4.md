# Revisión: *Acceleration of 1I/'Oumuamua from radiolytically produced H₂ in H₂O ice*

## 1. Información Bibliográfica
- **Título:** Acceleration of 1I/'Oumuamua from radiolytically produced H₂ in H₂O ice
- **Autores:** Jennifer B. Bergner¹,² y Darryl Z. Seligman³
- **Afiliaciones:** 
  ¹ Department of Chemistry, University of California, Berkeley, CA, USA
  ² Department of the Geophysical Sciences, University of Chicago, Chicago, IL, USA
  ³ Department of Astronomy and Carl Sagan Institute, Cornell University, Ithaca, NY, USA
- **Publicación:** *Nature*, Vol. 615, 23 marzo 2023, pp. 610–613
- **DOI:** https://doi.org/10.1038/s41586-022-05687-w
- **Fechas:** Recibido 30 septiembre 2022 / Aceptado 27 diciembre 2022 / Publicado en línea 22 marzo 2023
- **Repositorio de datos/código:** https://github.com/bergnerjb/Oumuamua_H2

## 2. Contexto y Objetivo del Estudio
El descubrimiento de 1I/'Oumuamua en 2017 presentó un conjunto de observaciones que incluyen: trayectoria hiperbólica confirmada, variación de brillo extrema (>2.5 mag), relación de ejes ≥6:1, espectro rojo sin características moleculares, ausencia de coma de polvo o gas detectable en longitudes de onda ópticas, centimétricas e infrarrojas, y una aceleración no gravitacional significativa con dependencia radial ~r⁻². La combinación de aceleración no gravitacional sin actividad cometaria observable ha generado múltiples hipótesis en la literatura.

El **objetivo específico** de este trabajo es evaluar cuantitativamente si la liberación de hidrógeno molecular (H₂) producido radiolíticamente a partir del procesamiento de hielo de H₂O por rayos cósmicos galácticos durante el viaje interestelar puede proporcionar la fuerza necesaria para explicar la aceleración no gravitacional observada en 'Oumuamua. El estudio se basa en resultados experimentales de laboratorio que demuestran la producción eficiente de H₂ a partir de hielo de H₂O bajo irradiación, y en la liberación de este H₂ atrapado durante el recocido térmico de la matriz de hielo amorfo en un rango de temperaturas de 15–140 K.

## 3. Metodología y Enfoque
- **Tipo de estudio:** Modelado numérico acoplado a datos experimentales de laboratorio, con análisis de presupuesto de masa y evolución térmica.
- **Datos y fuentes:**
  - *Observacionales de 'Oumuamua:* Solución orbital con aceleración no gravitacional A₁ = (4.92 ± 0.16) × 10⁻⁶ m s⁻² a 1 au (Micheli et al. 2018); dimensiones inferidas 115 × 111 × 19 m para albedo geométrico p = 0.1; límites superiores de producción de CN, H₂O, CO, CO₂ y polvo.
  - *Experimentales:* Resultados de laboratorio sobre producción de H₂ a partir de procesamiento de hielo de H₂O con diversas fuentes de energía (partículas energéticas, fotones UV, electrones), estructuras de hielo (cristalino y amorfo) y composiciones (hielo puro y mezclado).
- **Procedimiento analítico:**
  1. **Presupuesto de H₂:** Cálculo del número total de moléculas de H₂ necesarias para producir la aceleración observada entre 1.2 y 2.8 au, integrando la tasa de producción instantánea requerida a lo largo de la trayectoria.
  2. **Densidad volumétrica de H₂ en el cuerpo:** Estimación de la densidad de H₂ atrapado en función de la relación H₂:H₂O, la relación masa H₂O:polvo y la densidad bulk del objeto.
  3. **Criterio de viabilidad:** Comparación entre el número de moléculas de H₂ disponibles en una cáscara de desgasificación de espesor d y el número requerido para la aceleración, evaluando el espacio de parámetros (albedo, profundidad de desgasificación, temperatura de outflow, geometría del flujo, relaciones de abundancia).
  4. **Modelo térmico:** Resolución numérica de la ecuación de conducción de calor en coordenadas cilíndricas para determinar el perfil radial de temperatura durante el paso por el Sistema Solar, con condiciones de frontera que equilibran absorción solar, reradiación, calentamiento del material y difusión térmica.
  5. **Validación experimental:** Contrastación de los rangos de temperatura de liberación de H₂ (15–140 K) con los perfiles térmicos simulados para verificar que las profundidades requeridas para la desgasificación sean alcanzables.

## 4. Marco Teórico y Formalismo Matemático Clave
El artículo emplea los siguientes elementos formales:
- **Aceleración no gravitacional:** Modelada como a(r) = A₁ r⁻², con A₁ ≈ 4.92 × 10⁻⁶ m s⁻² a 1 au. La tasa de producción de masa Q se relaciona con la aceleración mediante:
  $$ M a(r) = \zeta Q v_{\text{H}_2} $$
  donde M es la masa del cuerpo, v_{H₂} es la velocidad térmica del H₂ outgaseado, y ζ representa la fracción del momento impartido en dirección anti-solar.
- **Velocidad térmica del H₂:** 
  $$ v_{\text{H}_2} = \sqrt{8 k_B T_{\text{H}_2} / \pi m_{\text{H}_2}} $$
- **Densidad volumétrica de H₂:**
  $$ n_{\text{H}_2} = (\rho_{\text{Bulk}} X_{\text{H}_2\text{O:dust}} X_{\text{H}_2:\text{H}_2\text{O}}) / m_{\text{H}_2\text{O}} $$
- **Número total de H₂ en cáscara de desgasificación:**
  $$ N_{\text{H}_2,\text{shell}} = \frac{4\pi}{3} n_{\text{H}_2} [r_a r_b r_c - (r_a-d)(r_b-d)(r_c-d)] $$
- **Criterio de viabilidad adimensional:**
  $$ \frac{N_{\text{H}_2,\text{shell}}}{N_{\text{H}_2,\text{accel}}} = \frac{(X_{\text{H}_2\text{O:dust}} X_{\text{H}_2:\text{H}_2\text{O}} m_{\text{H}_2}/m_{\text{H}_2\text{O}}) \rho_{\text{Bulk}} [1 - (1-d/r_a)(1-d/r_b)(1-d/r_c)]}{\zeta \int_{t_i}^{t_f} [a(\tau)/v_{\text{H}_2}] d\tau} $$
  Cuando esta razón > 1, el escenario es viable.
- **Ecuación de conducción de calor:**
  $$ \frac{\partial T}{\partial t} = \frac{\kappa}{\rho_{\text{Bulk}} c_P} \frac{\partial}{\partial r} \left( r \frac{\partial T}{\partial r} \right) $$
  con condición de frontera superficial que equilibra flujo solar absorbido, reradiación, calentamiento del material y difusión térmica.

## 5. Resultados Principales
1. **Viabilidad del mecanismo de H₂:** El criterio de viabilidad N_{H₂,shell}/N_{H₂,accel} > 1 se satisface para un amplio rango del espacio de parámetros esperados para un cuerpo tipo cometario. Para casos conservadores (T_{H₂} = 100 K, X_{H₂O:dust} = 1, X_{H₂:H₂O} = 0.3) y optimistas (T_{H₂} = 140 K, X_{H₂O:dust} = 3, X_{H₂:H₂O} = 0.4), el modelo es viable para profundidades de desgasificación de ~200–400 cm con albedos moderados (p ~ 0.1–0.3).
2. **Perfiles térmicos:** Para conductividades térmicas κ = 10⁻² y 10⁻¹ W K⁻¹ m⁻¹, las temperaturas de 15–140 K (rango de liberación de H₂) se alcanzan a profundidades de ~50–250 cm y ~8 m, respectivamente, durante el arco observacional (1.2–2.8 au). Esto indica que el núcleo puede calentarse a profundidades suficientes para explicar la extensión requerida de desgasificación de H₂.
3. **Tasa de producción de H₂:** Para T_{H₂} = 100 K y ζ = 0.75, la tasa de pérdida de masa de H₂ a 1.25 au varía entre ~10 y 800 g s⁻¹ para los extremos de albedo alto y bajo, respectivamente. Este valor es menor que estimaciones previas para H₂O debido a la menor masa molecular del H₂ y a diferentes supuestos sobre el tamaño del cuerpo.
4. **Consistencia con límites observacionales:** El mecanismo propuesto es compatible con los límites superiores de producción de CN, CO, CO₂ y polvo, ya que el H₂ no es detectable en las longitudes de onda utilizadas para las búsquedas de actividad en 'Oumuamua.
5. **Predicción observacional:** El modelo predice que cometas pequeños de período largo e interestelares deberían mostrar aceleraciones no gravitacionales análogas a 'Oumuamua al aproximarse al Sol, incluso si muestran actividad tenue o no detectable, debido a la desgasificación de H₂ desde capas superficiales a grandes distancias heliocéntricas (ej. hasta ~10–20 au).

## 6. Discusión y Análisis Descriptivo
El artículo integra resultados experimentales de laboratorio sobre procesamiento de hielo interestelar con modelado dinámico y térmico para proponer un mecanismo físico que reconcilia la aceleración no gravitacional de 'Oumuamua con la ausencia de actividad cometaria detectable. La propuesta se fundamenta en procesos genéricos: la producción radiolítica de H₂ a partir de H₂O es un fenómeno bien establecido experimentalmente bajo condiciones astrofísicamente relevantes, y la liberación de H₂ atrapado durante el recocido térmico ocurre en un rango de temperaturas amplio (15–140 K).

**Aspectos metodológicos destacados:**
- El enfoque de comparar el presupuesto de H₂ disponible con el requerido para la aceleración proporciona un criterio cuantitativo de viabilidad que puede evaluarse para diferentes combinaciones de parámetros inciertos (albedo, profundidad de desgasificación, temperatura de outflow, geometría del flujo).
- El modelo térmico emplea propiedades termofísicas típicas de núcleos cometarios (ρ_Bulk = 0.5 g cm⁻³, c_P = 2000 J kg⁻¹ K⁻¹, κ = 10⁻²–10⁻¹ W K⁻¹ m⁻¹) y explora extremos para evaluar la sensibilidad de los resultados.
- La consideración de la rotación compleja (tumbling) de 'Oumuamua justifica la suposición de que toda la superficie del cuerpo estuvo expuesta al Sol durante la trayectoria, permitiendo que la desgasificación ocurra desde toda la cáscara elipsoidal.

**Relación con observaciones:**
- La ausencia de detección de polvo micrométrico se discute en el contexto de que (i) el H₂ proporciona menos momento para arrastrar partículas de polvo que volátiles más pesados, (ii) interacciones con el medio interestelar pueden remover preferentemente granos pequeños de la superficie, y (iii) cuerpos más pequeños con gravedad propia débil pueden ser menos eficientes reteniendo polvo superficial.
- Los límites superiores de producción de H₂O derivados de observaciones de OH con el Green Bank Telescope (~30 kg s⁻¹ a 1.8 au) son considerablemente mayores que la producción requerida para la aceleración no gravitacional, por lo que la sublimación de H₂O no está excluida y, de estar activa, reduciría los rendimientos de H₂ necesarios.

**Contexto en la literatura:**
- El mecanismo propuesto se distingue de hipótesis que invocan la sublimación de volátiles puros (H₂, N₂, CO) al basarse en H₂ producido in situ a partir del procesamiento de H₂O, evitando inconsistencias teóricas u observacionales asociadas con la existencia y estabilidad de cuerpos compuestos predominantemente por estos volátiles.
- La propuesta es compatible con un origen natural de 'Oumuamua como planetesimal helado similar a cometas del Sistema Solar, sin requerir escenarios de formación altamente afinados.

## 7. Limitaciones, Preguntas Abiertas y Trabajo Futuro
**Limitaciones identificadas en el estudio:**
- **Parámetros inciertos:** El albedo geométrico, la profundidad efectiva de desgasificación, la temperatura del H₂ outgaseado, la geometría del flujo (colimado vs. isotrópico) y las relaciones de abundancia H₂:H₂O y H₂O:polvo no están constreñidos observacionalmente para 'Oumuamua, lo que requiere explorar un espacio de parámetros amplio.
- **Propiedades termofísicas:** La conductividad térmica, capacidad calorífica y densidad bulk se asumen por analogía con cometas del Sistema Solar; valores diferentes para 'Oumuamua alterarían los perfiles térmicos y las profundidades de liberación de H₂.
- **Rendimientos de H₂:** Los rendimientos H₂:H₂O de decenas de por ciento se basan en experimentos de laboratorio con muestras de espesor limitado; la extrapolación a cuerpos de escala cometaria (metros) introduce incertidumbre en la fracción de H₂ que escapa en diferentes regímenes de temperatura.
- **Evolución pre-perihelio:** El modelo considera únicamente el arco observacional (1.2–2.8 au post-perihelio); la posible desgasificación antes del perihelio depende de la historia térmica previa y de la posible presencia de una costra de baja conductividad que podría retrasar la propagación del calor.

**Preguntas abiertas:**
- ¿Cuál es la distribución real de rendimientos de H₂ para mezclas de hielos volátiles tipo cometario bajo dosis realistas de rayos cósmicos galácticos durante tiempos de viaje interestelar (~10⁶–10⁸ años)?
- ¿Cómo varía la eficiencia de liberación de H₂ con el espesor del hielo y la porosidad en condiciones relevantes para núcleos cometarios?
- ¿Puede la desgasificación de H₂ producir torques suficientes para explicar el estado de rotación no principal (tumbling) observado en 'Oumuamua?
- ¿Qué fracción de cometas pequeños del Sistema Solar o interestelares exhibiría aceleraciones no gravitacionales sin actividad detectable, y cómo se correlacionaría con su tamaño, composición y historia de irradiación?

**Trabajo futuro sugerido:**
- **Experimentos de laboratorio:** Medición sistemática de rendimientos de H₂ para diferentes tipos y dosis de procesamiento energético en hielos de H₂O puros y mezclas tipo cometario, incluyendo la fracción de H₂ que escapa en diferentes regímenes de temperatura para espesores de hielo relevantes.
- **Modelado termomecánico acoplado:** Desarrollo de simulaciones que incluyan la evolución de la porosidad, la formación de costras por sinterización y la retroalimentación entre desgasificación y estructura interna.
- **Observaciones de seguimiento:** Búsqueda de aceleraciones no gravitacionales en cometas pequeños de período largo e interestelares descubiertos por el LSST/Rubin Observatory, con sensibilidad a actividad tenue en radio/mm para detectar polvo grueso o líneas de OH/H₂O de alta resolución.
- **Caracterización de propiedades superficiales:** Estudios espectroscópicos y fotométricos de alta precisión para constreñir albedo, variabilidad espectral y estado de rotación en objetos pequeños, reduciendo degeneraciones en la inferencia de dimensiones y tasas de producción.

## 8. Conclusión General de la Revisión
El artículo de Bergner & Seligman (2023) presenta una propuesta física bien fundamentada para explicar la aceleración no gravitacional de 'Oumuamua mediante la liberación de H₂ producido radiolíticamente a partir de hielo de H₂O. El estudio integra de manera coherente resultados experimentales de laboratorio sobre procesamiento de hielos interestelares con modelado numérico de presupuesto de masa y evolución térmica, demostrando que el mecanismo es viable para un amplio rango de parámetros razonables para un cuerpo tipo cometario.

La propuesta tiene la ventaja de ser genérica: el procesamiento de H₂O por rayos cósmicos es un proceso universal que debería operar en cualquier cuerpo helado expuesto al medio interestelar, y la liberación de H₂ atrapado durante el calentamiento es un fenómeno termodinámico bien caracterizado. Además, el mecanismo es compatible con los límites observacionales de actividad en 'Oumuamua, ya que el H₂ no es detectable en las longitudes de onda empleadas para las búsquedas de gas y polvo.

El trabajo establece predicciones observacionales concretas que pueden ser validadas con futuros sondeos: pequeños cometas interestelares o de período largo deberían exhibir aceleraciones no gravitacionales sin actividad detectable si el mecanismo propuesto es correcto. En conjunto, el artículo contribuye al esfuerzo por comprender la diversidad de comportamientos dinámicos y físicos en cuerpos menores, y proporciona un marco cuantitativo para interpretar futuras detecciones de objetos interestelares con el LSST/Rubin Observatory y otras instalaciones de próxima generación.
