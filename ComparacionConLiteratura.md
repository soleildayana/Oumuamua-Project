# Comparativa entre el Desarrollo del Proyecto 'Oumuamua y el Estado del Arte en la Literatura

## Introducción

El miniproyecto documentado en `main.ipynb` representa un enfoque educativo y modular a la caracterización dinámica del primer objeto interestelar confirmado, 1I/'Oumuamua, utilizando herramientas computacionales modernas (pymcel) y metodología de dos cuerpos. En contraste, la carpeta `/Teoria` contiene ocho artículos de investigación que cubren aspectos especializados de 'Oumuamua: desde búsquedas de sistemas progenitores hasta mecanismos alternativos de formación y explicaciones de su aceleración no gravitacional.

Este documento sintetiza las convergencias, divergencias y complementariedades entre nuestro trabajo y la literatura revisada, estructurado en dimensiones temáticas clave.

---

## 1. Alcance y Objetivos

### Nuestro Proyecto (main.ipynb)

**Objetivos:**
- Recuperar efemérides reales de 'Oumuamua desde el servidor Horizons de NASA
- Caracterizar su órbita hiperbólica mediante conversión estado-elementos orbitales
- Calcular la dirección de llegada (radiant) en el cielo mediante análisis de las asíntotas orbitales
- Visualizar la trayectoria en contexto del Sistema Solar interior

**Alcance:**
- Tiempo computacional: ~10 Myr (integración hacia el pasado)
- Escala espacial: ~5 au (Sistema Solar interior)
- Complejidad dinámmica: problema de dos cuerpos (Sol + 'Oumuamua)
- Alcance científico: cinemática y geometría orbital

### Literatura Revisada

| Artículo | Alcance Principal | Escala Espacial | Tiempo Retropropagado |
|----------|------------------|-----------------|----------------------|
| Dybczyński & Królikowska (2018) | Búsqueda de progenitores con N-cuerpos débil | ~100 pc | ~250 Myr |
| Bailer-Jones et al. (2018) | Encuentros con Gaia DR2, potencial galáctico | ~50 pc (local) | ~100 Myr |
| Zuluaga et al. (2018) | Metodología probabilística de origen | ~100 pc | ~40 Myr |
| Zhang & Lin (2020) | Fragmentación tidal como origen | Sistema planetario | N/A (síntesis hacia futuro) |
| Zheng & Zhou (2025) | Formación por eyección planetaria | Sistema planetario | N/A (síntesis) |
| Jackson & Desch (2021, I-II) | Composición (N₂) y sustentabilidad | Medio interestelar | ~1 Gyr |
| Bergner & Seligman (2023) | Aceleración por H₂ radiolítico | Órbita heliocéntrica | N/A (síntesis) |
| ISSI Team (2019) | Síntesis integral | Galaxia + ISM | N/A (perspectiva) |

**Conclusión:** Nuestro proyecto ocupa el nicho educativo y de validación básica; la literatura cubre especializaciones complementarias que abarcan desde el origen hasta la composición.

---

## 2. Metodología Dinámica

### Nuestro Proyecto

```
Paso 1: Efemérides [Horizons] 
   ↓
Paso 2: Extracción estado heliocéntrico
   ↓
Paso 3: Cálculo elementos orbitales [pc.estado_a_elementos()]
   ↓
Paso 4: Análisis de asíntotas y dirección de llegada [Euler Z-X-Z]
   ↓
Paso 5: Visualización 3D [Plotly]
```

**Características:**
- Integración lineal (no integración de órbita completa)
- Marco heliocéntrico exclusivamente
- Tratamiento determinístico (solución nominal)
- Incertidumbres: no propagadas explícitamente

### Dybczyński & Królikowska (2018)

```
Órbita nominal + matriz covarianza [118 observaciones]
   ↓
Generación 10,000 clones [método Sitarski]
   ↓
Integración N-cuerpos en potencial galáctico [59 cuerpos]
   ↓
Preselección de perturbadores [3.5 pc]
   ↓
Refinamiento a 57 perturbadores + integración final
   ↓
Evaluación intervalos variación [±2-5% en d_min]
```

**Diferencias:**
- Propagación explícita de incertidumbres mediante clones
- Modelo dinámico N-cuerpos con 57 estrellas perturbadoras
- Potencial galáctico axisimétrico completo
- Resultados estadísticos (medianas, percentiles)

### Bailer-Jones et al. (2018)

```
Gaia DR2 (7.2M estrellas) + Sustitutos (2000 por estrella)
   ↓
Aproximación de Movimiento Lineal (LMA) [d < 10 pc]
   ↓
Integración orbital en potencial galáctico
   ↓
Distribuciones de encuentro [t_enc, d_enc, v_rel]
   ↓
Selección por d_enc < 2 pc y v_rel < mecanismo de eyección
```

**Ventaja sobre nosotros:**
- Catálogo 1000× más grande
- Cuantificación de incertidumbres estelares (2000 surrogates)
- Modelo de aceleración no gravitacional integrado

### Síntesis Comparativa

| Aspecto | Nuestro Proyecto | D&K 2018 | B-J 2018 |
|--------|------------------|----------|----------|
| Perturbadores explícitos | 1 (Sol) | 57 | ~7M preseleccionadas |
| Propagación incertidumbre | No | Sí (clones) | Sí (surrogates) |
| Potencial galáctico | No | Sí | Sí |
| Tiempo de cálculo | ~segundos | ~horas | ~horas |
| Reproducibilidad | Alta | Media | Baja (datos privativos) |

**Conclusión:** Nuestro proyecto es una "primer aproximación pedagógica"; la literatura implementa sofisticaciones dinámicas progresivas necesarias para búsquedas de progenitores rigurosas.

---

## 3. Tratamiento de Incertidumbres

### Nuestro Proyecto

- **Órbita:** solución nominal sin ensembles
- **Efemérides:** errores reportados por NASA, no propagados
- **Análisis:** determinístico (un radiant, una dirección)
- **Validación:** no explícita

**Limitación:**
Cambios de ~0.1° en RA/Dec (propios de la incertidumbre orbital) podrían desplazar el radiant estimado significativamente, alterando interpretaciones cualitativas sobre procesos de fragmentación o eyección.

### Literatura Revisada

#### Dybczyński & Królikowska (2018)
- 10,000 clones de 'Oumuamua
- Matriz de covarianza completa (JPL)
- Resultados: intervalos de ±2-5% en d_min
- **Hallazgo:** incertidumbres orbitales NO invalidan candidatos, pero DO afectan ranking

#### Bailer-Jones et al. (2018)
- 2,000 surrogates por estrella
- Covarianza 6D de Gaia + error en velocidades radiales
- Distribuciones de encuentro (percentiles 10-90)
- **Hallazgo:** HIP 3757 con d_enc = 0.60 pc (IC 90%: 0.53–0.67 pc) es robusto

#### Jackson & Desch (2021, Parte I)
- Albedo como variable libre (dos soluciones: p ≈ 0.12 y p ≈ 0.64)
- Sensibilidad analítica a composición y cohesión
- **Hallazgo:** degeneración albedo-tamaño; solución de alto albedo (p = 0.64) preferida por analogía con Pluto

#### Zuluaga et al. (2018)
- 10,000 clones de 'Oumuamua + múltiples clones estelares
- Kernel de suavizado gaussiano para densidad numérica (h ≈ 0.5 pc)
- **Hallazgo:** sensibilidad ~±10-30% en d_min, pero ranking de candidatos robusto

### Síntesis

| Método | Alcance | Robustez |
|--------|---------|----------|
| Nuestro (nominal) | Cualitativa | Baja; cambios ±0.1° en RA/Dec alteran conclusiones |
| Ensemble orbita solo | Cuantitativa parcial | Media; acota variación en encuentros |
| Ensemble bidireccional | Cuantitativa completa | Alta; JD 2018, Z&Z 2018 implementan |

**Conclusión:** Para búsquedas de progenitores defensibles, es **necesario** propagar incertidumbres en ambas direcciones; nuestro proyecto identifica su importancia pero no la implementa computacionalmente.

---

## 4. Elementos Orbitales vs. Composición

### Nuestro Proyecto

```
Cálculo de elementos orbitales (p, e, i, Ω, ω, f) desde estado heliocéntrico
   ↓
Clasificación: hiperbólica (e = 1.205)
   ↓
Derivación: f_∞ ≈ 146° (anomalía verdadera al infinito)
   ↓
Geometría hiperbólica: direction de llegada (radiant)
```

**Enfoque:** Puramente cinemático. Establece "de dónde llegó" geometricamente, pero **no aborda cómo se movió durante el paso solar o qué mecanismo explica la aceleración no gravitacional**.

### Zhang & Lin (2020) – Fragmentación Tidal

**Propuesta:** 'Oumuamua es un fragmento producido por ruptura tidal durante encuentro cercano con su estrella natal.

**Mecanismo:**
1. Planetesimal de ~10-100 m pasa a distancia < d_Roche de la estrella
2. Fuerzas de marea lo fragmentan en piezas prolatas (~100 m)
3. Recondensación superficial de silicatos crea costra desecada tipo asteroidal
4. Retención de volátiles (H₂O, CO₂) en profundidades ~0.1-0.5 m
5. Eyección a baja velocidad relativa (~10 km/s) por interacción ISM + campos magnéticos

**Conexión con nuestro proyecto:** Explica la forma elongada (e = 1.205 observado) sin requerimientos de tuning, pero requiere retropropagación dinámico-térmica más allá de nuestro alcance.

### Jackson & Desch (2021, Partes I-II) – Hipótesis N₂

**Propuesta alternativa:** 'Oumuamua es un fragmento de hielo de N₂ de la superficie de un cuerpo tipo Pluto en otro sistema estelar.

**Elementos nuevos:**
- Aceleración no gravitacional explicada por sublimación de N₂ (no H₂O)
- Albedo ~0.64 (consistente con superficies de Pluto/Tritón)
- Dimensiones: 45 m × 44 m × 7.5 m (compatible con potencia aparente)
- Masa inicial ~8 × 10⁶ kg (consistente con erosión interestelar ~1 Gyr)
- Eyección de ~0.074 M⊕ durante inestabilidad tipo "Nice model" en el Cinturón de Kuiper primordial

**Diferencia del nuestro:** Añade composición específica y mecanismo de eyección (inestabilidad dinámica, no fragmentación tidal).

### Bergner & Seligman (2023) – H₂ Radiolítico

**Propuesta alternativa:** Aceleración explica por H₂ producido radiolíticamente en el hielo de H₂O durante tránsito interestelar.

**Mecanismo:**
- Rayos cósmicos galácticos procesan H₂O en el interior del objeto
- H₂ es producido con rendimiento ~30% en Myr
- Liberación ocurre entre 15–140 K durante recocido térmico en el Sistema Solar
- Velocidad térmica del H₂ (~1 km/s) proporciona momento para la aceleración observada

**Ventaja:** Explica aceleración sin requerir H₂O o CO detectable en la superficie.

### Síntesis: Mecanismos de Aceleración

| Mecanismo | Autor(es) | Aceleración Explicada | Observaciones Consistentes | Problemas |
|-----------|-----------|----------------------|--------------------------|-----------|
| Sublimación H₂O | Estándar | Sí | Límites CN/CO altos | Sin detección, retraso térmico |
| H₂ radiolítico | Bergner & Seligman | Sí | Ausencia H₂O observable | No observación directa de H₂ |
| N₂ puro | Jackson & Desch | Sí | Albedo, tasa masa | Especulativo sobre origen |
| Presión de radiación | Especulativo | Marginal | Ninguna | Refutado por fotometría (ISSI) |

**Conclusión:** Nuestro proyecto establece la cinemática orbital, pero la **composición y mecanismo de aceleración permanecen ambiguos**. La literatura propone tres hipótesis físicamente plausibles, cada una con fortalezas y limitaciones.

---

## 5. Búsqueda de Sistemas Progenitores

### Nuestro Proyecto

- **Método:** Cálculo del radiant (dirección de llegada en el cielo)
- **Resultado:** Coordenadas ecuatoriales (RA, Dec) desde las cuales 'Oumuamua aparenta haber llegado
- **Uso:** Identifica dirección, NO identifica estrella específica
- **Limitación:** Retropropagación cinemática pura sin dinámica galáctica

### Dybczyński & Królikowska (2018)

**Método:**
- Integración de 'Oumuamua + 57 estrellas en potencial galáctico
- Identificación de encuentros cercanos (d_min < 1 pc)
- Resultado: **7 encuentros con d_min < 1 pc**

**Candidatos principales:**
1. HIP 3757: d_min = 0.044 pc, t = −0.118 Myr, v_rel = 185.4 km/s
2. GJ 4274: d_min = 0.412 pc, t = −0.023 Myr, v_rel = 309.5 km/s
3. HIP 113020 (GJ 876): **d_min = 2.241 pc, v_rel = 3.927 km/s, 4 planetas confirmados**

**Crítica:** GJ 876 es atractivo (v_rel baja sugiere eyección planetaria), pero la distancia (~2.2 pc) es marginal.

### Bailer-Jones et al. (2018)

**Método:**
- Gaia DR2 (7.2M estrellas)
- Aproximación lineal (LMA) + integración orbital
- 2000 surrogates por estrella para incertidumbre
- Criterio: d_enc < 2 pc, v_enc plausible para eyección

**Candidatos principales:**
1. **HIP 3757**: d_enc = 0.60 pc (IC: 0.53–0.67), v_enc = 24.7 km/s, distancia hoy ~3.2 pc
2. HD 292249: d_enc = 1.60 pc, v_enc = 10.7 km/s (baja velocidad relativa)
3. HIP 113020 (GJ 876): d_enc = 2.241 pc, v_enc = 3.927 km/s

**Novedad:** Incorpora aceleración no gravitacional (corrige trayectoria ~0.4°) → valida HIP 3757 sobre otros candidatos previos

### Zuluaga et al. (2018)

**Método:**
- Probabilidad de Origen Interestelar (IOP): P(estrella sea progenitor | datos)
- Componentes: Ppos (coincidencia espacial) × f_ind (velocidad eyección)
- Catálogo AstroRV: 285,114 estrellas

**Candidatos con máxima IOP:**
1. **HIP 103749 (HD 200325)**: t_enc = −4.22 Myr, d_enc = 1.75 pc, v_rel = 12.0 km/s, sistema binario
2. TYC 3144-2040-1: d = 4.5 pc, v_rel = 17.9 km/s
3. η Cas (HIP 3821): d = 6.0 pc, v_rel = 23.5 km/s
4. GJ 876 (HIP 113020): d = 3.5 pc, v_rel = 36.8 km/s

**Método distintivo:** Incorpora probabilidad de que un encuentro cercano corresponda a eyección real (no encuentro por azar).

### Síntesis: Búsqueda de Progenitores

| Candidato | D&K 2018 | B-J 2018 | Z&Z 2018 | Consenso |
|-----------|----------|----------|----------|----------|
| HIP 3757 | Muy cercano (0.044 pc) | Robusto (0.60 pc, IC) | Ausente | Alto; pero v_rel = 25 km/s sugiere difícil de eyectar |
| GJ 876 | 2.24 pc, v_rel = 3.9 km/s | 2.24 pc, v_rel = 3.9 km/s | v_rel = 36.8 km/s | Prometedor (baja v_rel, planetas confirmados) |
| HIP 103749 | No reportado | No reportado | Máxima IOP | Probado con métodos bayesianos |

**Conclusión:** La literatura identifica 3-4 candidatos plausibles, pero **ninguno es definitivo**. La variedad de métodos (D&K, B-J, Z&Z) produce candidatos parcialmente distintos, reflejando degeneraciones inherentes al problema inverso. Nuestro proyecto **no identifica candidatos específicos**, pero establece que el análisis requiere integración galáctica y propagación de incertidumbres completa.

---

## 6. Composición y Mecanismos Físicos

### Nuestro Proyecto

**No aborda:** Composición específica, mecanismo de aceleración, o procesos termofísicos durante el paso solar.

### Zhang & Lin (2020) – Fragmentación Tidal

**Hallazgos clave:**
- Forma prolata (relación ~1:6) es producto natural de ruptura tidal
- Costra desecada resulta de fusión/recondensación de silicatos (3 h post-periastrón)
- Retención de volátiles en profundidades ~0.1-0.5 m explica ausencia de coma
- Rotación caótica ("tumbling") se mantiene por amortiguamiento bajo en fragmentos de ~100 m

**Simulaciones N-cuerpos:** Elemento de disco blando (~20,000 partículas) que sufre fragmentación tidal bajo el potencial gravitacional de una estrella de 0.5 M☉.

**Predicción poblacional:** ~1-3% de ISOs pequeños (~100 m) deberían ser fragmentos tipo 'Oumuamua.

### Jackson & Desch (2021, Parte I)

**Hipótesis:** 'Oumuamua es fragmento de N₂ con albedo p = 0.64.

**Justificación:**
- N₂ es el único hielo (de 9 evaluados: H₂, Ne, CH₄, CO, N₂, NH₃, O₂, CO₂, H₂O) que reproduce A₁ para p realista
- Albedo p = 0.64 coincide con superficies de Pluto (p = 0.62 ± 0.03) y Tritón
- Dimensiones infieren: 45.5 m × 43.9 m × 7.5 m
- Pérdida de masa: ~0.37 kg/s, muy por debajo de límites observacionales

**Validación:** Erosión interestelar por GCR es ~6.6 m/Gyr; tránsito de 0.4-0.5 Gyr implica erosión ~10 m, consistente con masa inicial deducida.

### Jackson & Desch (2021, Parte II)

**Extensión:** ¿Puede el Nice model generar suficientes fragmentos de N₂?

**Hallazgos:**
- Inestabilidad dinámica del Cinturón de Kuiper primordial produce ~0.074 M⊕ de ejecta
- ~60% (~0.043 M⊕) es hielo de N₂ de capas superficiales
- Con distribución de tamaños q ≈ 6 y D_min = 50 m → ~2.7 × 10¹⁵ fragmentos iniciales
- Eficiencia de eyección interestelar: ~18% de fragmentos de N₂ alcanzan ISM
- **Densidad interestelar predicha:** ~1.4 × 10¹² pc⁻³ (fragmentos de N₂)

**Comparación con observación:** Densidad inferida de ISOs es ~0.1 au⁻³ = ~1.6 × 10¹⁵ pc⁻³. La hipótesis de N₂ + distribución de tamaños realista reconcilia densidad observada con tasas de eyección plausibles (~0.004-3 M⊕ pc⁻³).

### Bergner & Seligman (2023) – H₂ Radiolítico

**Mecanismo de aceleración:**
- Rayos cósmicos galácticos procesan H₂O → H₂ con rendimiento ~30%
- Liberación ocurre entre 15–140 K durante recocido térmico heliocéntrico
- Velocidad térmica: v_H₂ = √(8kT/πm) ~ 1 km/s
- Profundidad de desgasificación requerida: ~200–400 cm (alcanzable con κ = 10⁻² W K⁻¹ m⁻¹)

**Viabilidad:**
- Presupuesto de H₂: ~10¹⁵–10²⁵ moléculas requeridas
- Densidad volumétrica: compatible con X_H₂:H₂O ~ 0.3-0.4, típico de hielos interestelares
- Compatibilidad con límites observacionales de CO, CO₂, polvo: verificada (H₂ no detectable)

**Ventaja:** Explicar aceleración sin requerir H₂O detectable.

### Síntesis: Modelos Composicionales

| Modelo | Autor(es) | Composición | Mecanismo de Aceleración | Viabilidad | Problemas |
|--------|-----------|-------------|--------------------------|-----------|----------|
| H₂O estándar | Múltiples | ~100% H₂O | Sublimación | Alta | Ausencia coma detectable |
| N₂ puro | J&D | ~100% N₂ | Sublimación N₂ | Media | Origen especulativo, pero consistente |
| H₂ radiolítico | B&S | H₂O + H₂ producido | Desgasificación H₂ | Media-Alta | Sin observación directa de H₂ |
| Fragmento tidal | Z&L | Silicatos + volátiles profundos | H₂O u otro volátil | Alta | Forma extrema requiere condiciones |

**Conclusión:** Nuestro proyecto **no discrimina entre modelos composicionales**. La literatura propone cuatro hipótesis físicamente plausibles, cada una validable o refutable con observaciones futuras (espectroscopía IR sensible a N₂ vs. H₂O, emisión de polvo grueso, etc.).

---

## 7. Escala Poblacional: De 'Oumuamua a Estadística Galáctica

### Nuestro Proyecto

**Alcance poblacional:** Ninguno. Enfoque en un objeto.

### Literatura: Crecimiento Progresivo de Escala

#### Dybczyński & Królikowska (2018)
- Pregunta: ¿Cuántos encuentros cercanos ha tenido 'Oumuamua?
- Respuesta: 7 con d < 1 pc, pero probables "falsos positivos"
- Contexto: Un objeto, búsqueda de progenitor

#### Bailer-Jones et al. (2018) – Gaia DR2
- Pregunta: ¿Quéstrellas cercanas son estadísticamente compatibles con ser progenitor?
- Innovación: Incorpora aceleración no gravitacional en órbita nominal
- Resultado: 4 candidatos principales, ranking de probabilidades relativas
- Contexto: Del objeto singular a contexto estelar local

#### Zuluaga et al. (2018) – Metodología Probabilística
- Pregunta: ¿Cómo cuantificar que una estrella sea el origen?
- Innovación: IOP = P_pos × f_ind, separando probabilidad espacial de física de eyección
- Resultado: Metodología reproducible y actualizable con Gaia DR3/4
- Herramienta pública: paquete iWander
- Contexto: Del ranking ad hoc a marco bayesiano

#### Zhang & Lin (2020) – Formación de Población
- Pregunta: ¿Si 'Oumuamua es fragmento tidal, cuántos debería haber?
- Innovación: Simulaciones N-cuerpos de fragmentación + estadística de eyección
- Resultado: ~1-3% de ISOs pequeños deberían ser fragmentos tipo 'Oumuamua
- Contexto: De objeto singular a población galáctica

#### Jackson & Desch (2021, Parte II) – Presupuesto de Masa
- Pregunta: ¿Cuántos fragmentos de N₂ produce una inestabilidad tipo Nice model?
- Innovación: Modelado de colisiones KBO + sinterización superficial + erosión GCR
- Resultado: Densidad predicha ~1.4 × 10¹² pc⁻³ (fragmentos de N₂), consistente con densidad total inferida
- Contexto: De pregunta sobre un objeto a validación de mecanismo de producción galáctica

#### ISSI Team (2019) – Síntesis y Perspectiva
- Pregunta: ¿Son todas las propiedades de 'Oumuamua naturales o exigen explicaciones exóticas?
- Resultado: Todas las propiedades son consistentes con un origen natural
- Argumento poblacional: La densidad de ISOs no es anómala si se considera SFD realista
- Contexto: De debate sobre 'Oumuamua a framework para era LSST

### Síntesis Poblacional

```
'Oumuamua (objeto singular)
    ↓
¿Sistema progenitor? (Dybczyński, Bailer-Jones, Zuluaga)
    ↓
¿Mecanismo de formación? (Zhang & Lin)
    ↓
¿Abundancia galáctica? (Jackson & Desch, ISSI Team)
    ↓
Predicción para LSST: ~1 ISO/año
```

**Conclusión:** Nuestra proyecto trata un objeto aislado. La literatura progresa desde búsquedas de progenitor hacia construcción de modelos poblacionales validables con futuros sondeos. El Vera C. Rubin Observatory (LSST, operación ~2025 en adelante) transformará el campo de caso singular a estadística de poblaciones.

---

## 8. Métodos Computacionales y Herramientas

### Nuestro Proyecto

| Herramienta | Uso |
|-------------|-----|
| `pymcel` | Conversión estado-elementos, consultas Horizons, visualización 3D |
| NumPy/SciPy | Operaciones vectoriales, matriz de rotación (Euler) |
| Plotly | Visualización interactiva 3D |
| SPICE (spiceypy) | No utilizado aquí, pero disponible en pymcel |

**Característica:** Enfoque integrado, código breve (~50-100 líneas útiles), alta legibilidad educativa.

### Literatura

| Artículo | Herramientas | Escala Computacional |
|----------|--------------|----------------------|
| Dybczyński & Królikowska | Integrador N-cuerpos personalizado, potencial galáctico analítico | ~horas (59 cuerpos, 10k clones) |
| Bailer-Jones et al. | REBOUND + SpiceIKY, Gaia tools | ~horas (7.2M estrellas, 2k surrogates c/u) |
| Zuluaga et al. | iWander (C/C++/Python, paquete público) | ~minutos a horas (285k estrellas) |
| Zhang & Lin | PKDGRAV (N-cuerpos, elemento discreto), modelado térmico acoplado | ~días (20k partículas, dinámica + termo) |
| Jackson & Desch | Modelado analítico-numérico, integración térmica 1D | ~horas (evaluación paramétrica) |
| Bergner & Seligman | Modelado térmico 1D, integración orbital Keplerian | ~minutos (modelo químico-térmico) |

**Tendencia:** Escala computacional crece con complejidad dinámica. Nuestro proyecto utiliza herramientas de "caja negra" de alto nivel (pymcel), mientras que literatura implementa modelos especializados.

### Reproducibilidad

| Proyecto | Código Público | Datos Públicos | Reproducible |
|----------|--------|-------|-------|
| Nuestro | Aquí (GitHub) | NASA Horizons | Sí, sin restricciones |
| iWander (Z&Z) | GitHub (https://github.com/seap-udea/iWander) | AstroRV | Sí |
| REBOUND (B-J) | No explícitamente | Gaia DR2 (público) | Parcial (necesita Gaia download) |
| PKDGRAV (Z&L) | No | Parámetros en paper | Parcial (código especializado) |
| Jackson & Desch | Repositorio Zenodo | Tablas en paper | Sí (datos + script analítico) |

**Conclusión:** Nuestro proyecto tiene **ventaja en reproducibilidad inmediata**; la literatura requiere acceso a catálogos grandes o códigos especializados.

---

## 9. Preguntas Científicas Abiertas

### Jerarquía de Incertidumbres (de más a menos resuelta)

| Pregunta | Nuestro Proyecto | Literatura | Estatus |
|----------|------------------|-----------|---------|
| ¿Cómo llegó 'Oumuamua? (trayectoria) | **Respondida** | Confirmada/extendida | **Resuelto** |
| ¿De dónde vino? (dirección en cielo) | **Respondida** | Confirmada/extendida | **Resuelto** |
| ¿Quién es el progenitor? (estrella específica) | No abordado | 3-4 candidatos, sin consenso | **Abierto** |
| ¿Por qué la forma alargada? | No abordado | Z&L: fragmentación tidal; especulación | **Parcialmente resuelto** |
| ¿Cuál es la composición? | No abordado | J&D: N₂; B&S: H₂O + H₂; debate abierto | **Abierto** |
| ¿Cómo se explica la aceleración no gravitacional? | No abordado | 3 mecanismos plausibles | **Abierto** |
| ¿Cuántos ISOs hay? | No abordado | ~0.1 au⁻³ inferido; debate sobre SFD | **Parcialmente resuelto** |
| ¿Cuál es el mecanismo de eyección galáctica? | No abordado | Z&L, J&D: fragmentación + dinámicas múltiples | **Parcialmente resuelto** |

### Líneas de Investigación Futuras Identificadas en Literatura

1. **Observaciones directas:** Espectroscopía IR de JWST para detectar N₂, volátiles específicos, composición isotópica → Jackson & Desch, Bergner & Seligman
2. **Catálogos estelares mejorados:** Gaia DR4 (2026+) → reduciría incertidumbres en búsquedas de progenitor (Bailer-Jones)
3. **Poblaciones de ISOs:** LSST ~1 ISO/año → estadística de tamaños, composición, cinemática → ISSI Team, Zhang & Lin
4. **Modelado de sistemas exoplanetarios:** Simulaciones de Nice model con arquitecturas variables → Jackson & Desch II
5. **Análogos del Sistema Solar:** Estudios de cometas de período largo, objetos Manx para calibrar límites de actividad → ISSI Team
6. **Termodinámica de volátiles interestelaes:** Experimentos de laboratorio sobre erosión por GCR, fotodesorción → Jackson & Desch, Bergner & Seligman

---

## 10. Síntesis y Posicionamiento de Nuestro Proyecto

### Fortalezas Relativas

| Aspecto | Nuestro Proyecto | Literatura |
|--------|------------------|-----------|
| **Accesibilidad pedagógica** | ⭐⭐⭐⭐⭐ | ⭐⭐ |
| **Reproducibilidad inmediata** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |
| **Integración numérica rigurosa** | ⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Exploración del espacio de parámetros** | ⭐ | ⭐⭐⭐⭐⭐ |
| **Propagación de incertidumbres** | ⭐ | ⭐⭐⭐⭐ |
| **Modelado composicional** | ⭐ | ⭐⭐⭐⭐ |
| **Búsqueda de progenitores** | ⭐ | ⭐⭐⭐⭐ |

### Ubicación en la Literatura

```
Escala de Complejidad Dinámica:

Nivel 1 (Nuestro Proyecto)
├─ Problema de dos cuerpos
├─ Heliocéntrico
├─ Sin potencial galáctico
└─ Determinístico (sin ensembles)

Nivel 2 (Dybczyński & Królikowska)
├─ N-cuerpos débil (57 perturbadores)
├─ Potencial galáctico axisimétrico
├─ Propagación incertidumbre 'Oumuamua
└─ Resultados estadísticos

Nivel 3 (Bailer-Jones, Zuluaga)
├─ Catálogos estelares masivos (7M + 285k)
├─ Probabilidades de origen (IOP, densidades)
├─ Propagación bidireccional
└─ Metodología reproducible

Nivel 4 (Zhang & Lin, Jackson & Desch, Bergner & Seligman)
├─ Simulaciones N-cuerpos de formación
├─ Modelado termofísico acoplado
├─ Estadística poblacional galáctica
└─ Validación de mecanismos
```

### Nichos de Contribución

| Proyecto | Nicho | Valor Científico | Valor Educativo |
|----------|------|------------------|-----------------|
| **Nuestro** | Validación de herramientas educativas (pymcel) | Bajo (derivativo) | **Alto** |
| **Dybczyinski & Królikowska** | Búsqueda sistemática en radio local | **Alto** | Medio |
| **Bailer-Jones et al.** | Metodología estadística + Gaia | **Alto** | Medio |
| **Zhang & Lin** | Unificación de morfología + mecánica | **Muy Alto** | Bajo (especializado) |
| **Jackson & Desch** | Hipótesis alternativa (N₂) + población | **Muy Alto** | Bajo (especializado) |
| **Bergner & Seligman** | Mecanismo químico-físico de aceleración | **Alto** | Bajo (especializado) |
| **ISSI Team** | Síntesis y refutación de exotismo | **Alto** | **Muy Alto** |

### Síntesis Final

Nuestro proyecto en `main.ipynb` constituye un **puente pedagógico accesible e inmediatamente reproducible** que realiza las operaciones básicas de caracterización dinámica de 'Oumuamua: recuperación de efemérides, cálculo de elementos orbitales, y derivación de la dirección de llegada (radiant) en el cielo. Estas son **operaciones necesarias pero no suficientes** para una investigación completa.

La literatura revisada construye sobre estos fundamentos mediante:

1. **Extensión dinámica:** Integración en potenciales galácticos realistas, inclusión de perturbadores estelares múltiples
2. **Cuantificación de incertidumbres:** Propagación bidireccional (órbita + estrellas), análisis probabilísticos
3. **Búsqueda de origen:** Identificación de candidatos progenitores, metodologías de ranking (Bailer-Jones, Zuluaga)
4. **Mecanismos de formación:** Simulaciones de fragmentación tidal, inestabilidad dinámica, eyección galáctica
5. **Composición y física:** Análisis termofísico, modelos de aceleración no gravitacional, hipótesis alternativas
6. **Estadística galáctica:** Predicciones poblacionales, reconciliación de densidades numéricas inferidas
7. **Síntesis y perspectiva:** Refutación de hipótesis exóticas, establecimiento del framework para era LSST

**En conclusión:** Nuestro trabajo es **complementario, no competitivo** con la literatura. Representa el escalón inicial en una escalera de complejidad creciente, donde cada peldaño responde preguntas sucesivas: "¿De dónde vino?", "¿Quién es el progenitor?", "¿Cómo se formó?", "¿Cuántos hay?". Juntos, estos trabajos—desde lo pedagógico hasta lo especializado—construyen una comprensión multidimensional del primer visitante interestelar confirmado.

---

## Referencias Cruzadas

- **Nuestro proyecto:** Nivel educativo; cinemática heliocéntrica
- **Dybczyński & Królikowska (2018):** Búsqueda de progenitor; 59B model
- **Bailer-Jones et al. (2018):** Gaia DR2; aceleración no gravitacional
- **Zuluaga et al. (2018):** Probabilidades de origen; iWander
- **Zhang & Lin (2020):** Fragmentación tidal; población
- **Zheng & Zhou (2025):** Eyección planetaria; viabilidad
- **Jackson & Desch (2021):** Hipótesis N₂; presupuesto de masa
- **Bergner & Seligman (2023):** H₂ radiolítico; aceleración
- **ISSI Team (2019):** Síntesis integral; refutación de exotismo
