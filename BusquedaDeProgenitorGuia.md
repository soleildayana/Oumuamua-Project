# Cómo Desarrollar una Sección de Búsqueda de Progenitor

---

## **Nivel 1: Búsqueda por Radiant (Más Simple)**

Esto utiliza la dirección de llegada que ya calculaste:

```python
## Búsqueda de Progenitor - Nivel 1: Análisis por Radiant

# El radiant ya calculado
print(f"Radiant de 'Oumuamua: RA = {ra_from:.2f}°, Dec = {dec_from:.2f}°")
print(f"\nBuscando estrellas cercanas en la dirección opuesta del radiant...")

# Cargar catálogo de estrellas cercanas (ej. Gaia)
# Filtrar por:
# 1. Proximidad angular al radiant (radio de búsqueda, ej. 30°)
# 2. Distancia actual < 100 pc
# 3. Velocidad compatible con mecanismo de eyección (v_rel < 50 km/s)

radius_search = 30  # grados
candidates = []

print(f"\nCriterios de búsqueda:")
print(f"- Radio de búsqueda angular: ±{radius_search}°")
print(f"- Distancia actual: < 100 pc")
print(f"- Velocidad relativa: < 50 km/s (eyección plausible)")
```

**Ventaja:** Conceptualmente simple, sin necesidad de integración orbital compleja.
**Desventaja:** No considera la dinámica galáctica ni la retropropagación temporal.

---

## **Nivel 2: Aproximación de Movimiento Lineal (LMA) - Intermedio**

```python
## Búsqueda de Progenitor - Nivel 2: LMA (Movimiento Lineal)

def linear_motion_approximation(r_object, v_object, r_star, v_star, t_max=100):
    """
    Aproximación de movimiento lineal para encontrar encuentro mínimo
    
    Args:
        r_object: posición heliocéntrica de 'Oumuamua (km)
        v_object: velocidad heliocéntrica de 'Oumuamua (km/s)
        r_star: posición heliocéntrica de estrella candidata (km)
        v_star: velocidad heliocéntrica de estrella (km/s)
        t_max: tiempo máximo a retropropagar (Myr)
    
    Returns:
        dict con t_enc, d_min, v_rel
    """
    import numpy as np
    
    # Convertir tiempo a segundos
    t_max_s = t_max * 1e6 * 365.25 * 24 * 3600
    
    # Vectores relativos en t=0
    dr = r_star - r_object
    dv = v_star - v_object
    
    # Parámetros de encuentro mínimo: t = -(dr·dv) / |dv|²
    if np.linalg.norm(dv) < 1e-6:
        return None  # velocidades casi iguales
    
    dot_product = np.dot(dr, dv)
    dv_squared = np.dot(dv, dv)
    
    t_enc_s = -dot_product / dv_squared
    
    # Distancia mínima
    r_min = dr + dv * t_enc_s
    d_min_km = np.linalg.norm(r_min)
    d_min_pc = d_min_km / (pc.constantes.pc / 1000)  # convertir a parsecs
    
    # Velocidad relativa
    v_rel = np.linalg.norm(dv)
    
    # Convertir tiempo a Myr
    t_enc_myr = t_enc_s / (1e6 * 365.25 * 24 * 3600)
    
    return {
        't_enc': t_enc_myr,
        'd_min': d_min_pc,
        'v_rel': v_rel,
        'viable': d_min_pc < 2.0 and v_rel < 50  # criterios de plausibilidad
    }

# Ejemplo con una estrella hipotética
r_star_example = np.array([1.5e8, -7e7, 1e7]) * 1e3  # en metros
v_star_example = np.array([20, 10, 5])  # km/s

result = linear_motion_approximation(r0, v0, r_star_example, v_star_example)
print(f"Encuentro mínimo: {result['d_min']:.2f} pc hace {abs(result['t_enc']):.2f} Myr")
print(f"Velocidad relativa: {result['v_rel']:.1f} km/s")
print(f"¿Viable? {result['viable']}")
```

**Ventaja:** Más preciso, sin integración completa (rápido).
**Desventaja:** Aún ignora potencial galáctico.

---

## **Nivel 3: Integración Orbital Completa (Más Sofisticado)**

```python
## Búsqueda de Progenitor - Nivel 3: Integración en Potencial Galáctico

# Requiere: scipy, potencial galáctico analítico

def galactic_potential(position_gc):
    """
    Potencial gravitacional galáctico axisimétrico (Irrgang et al. 2013)
    
    Args:
        position_gc: posición en coordenadas galactocéntricas (x, y, z) en pc
    
    Returns:
        potencial Φ en (km/s)²
    """
    import numpy as np
    
    # Parámetros del modelo (Irrgang et al. 2013)
    M_disk = 1.0e11  # M_sun
    M_bulge = 1.7e10
    M_halo = 1.2e12
    
    a_disk = 6500  # pc
    a_bulge = 3500
    
    x, y, z = position_gc
    R = np.sqrt(x**2 + y**2)
    
    # Potencial del disco (Miyamoto-Nagai)
    Phi_disk = -pc.constantes.G * M_disk / np.sqrt(R**2 + (a_disk + np.sqrt(z**2 + a_disk**2))**2)
    
    # Similar para bulbo y halo (simplificado)
    Phi_bulge = -pc.constantes.G * M_bulge / np.sqrt(R**2 + (a_bulge + np.sqrt(z**2 + a_bulge**2))**2)
    Phi_halo = -pc.constantes.G * M_halo / np.sqrt(R**2 + z**2 + 5000**2)
    
    return (Phi_disk + Phi_bulge + Phi_halo) * 1e-6  # convertir a (km/s)²

# Integrar órbita hacia atrás (opcional: usar scipy.integrate.odeint)
print("""
NOTA: Para una integración completa se requeriría:
1. Convertir posiciones heliocéntricas → galactocéntricas
2. Usar integrador de tipo RK45 (scipy.integrate.solve_ivp)
3. Iterar sobre múltiples estrellas del catálogo
4. Calcular encuentros para cada una

Esto es computacionalmente intensivo pero da máxima precisión.
""")
```

---

## **Recomendación: Enfoque Híbrido Educativo**

Para tu miniproyecto, sugiero combinar **Nivel 1 + Nivel 2**:

```python
## SECCIÓN COMPLETA PARA AGREGAR A main.ipynb

# ============================================================================
# BÚSQUEDA DE PROGENITOR
# ============================================================================

## 1. Caracterización del espacio de búsqueda

print("="*70)
print("BÚSQUEDA DE SISTEMA PROGENITOR DE 'OUMUAMUA")
print("="*70)

print(f"\nRadiant de llegada (dirección desde la cual vino):")
print(f"  RA = {ra_from:.2f}° | Dec = {dec_from:.2f}°")
print(f"\nVelocidad asintótica respecto al Sol:")
v_inf = np.sqrt(ere * 2)  # energía específica → velocidad asintótica
print(f"  v_∞ = {v_inf:.2f} km/s")

## 2. Critarios de selección de candidatos

print(f"\n{'─'*70}")
print("CRITERIOS DE BÚSQUEDA:")
print(f"{'─'*70}")

criteria = {
    'distancia_actual': ('< 100 pc', 'cercana al Sistema Solar hoy'),
    'distancia_encuentro': ('< 2 pc', 'encuentro cercano en el pasado'),
    'velocidad_relativa': ('< 50 km/s', 'compatible con eyección'),
    'tiempo_retropropagado': ('< 100 Myr', 'historia dinámica reciente'),
}

for criterion, (value, reason) in criteria.items():
    print(f"  • {criterion.replace('_', ' ').title()}: {value}")
    print(f"    → {reason}")

## 3. Conexión con la literatura

print(f"\n{'─'*70}")
print("CONEXIÓN CON LITERATURA:")
print(f"{'─'*70}")
print("""
Este enfoque sigue la metodología de:

Bailer-Jones et al. (2018):
  - Aproximación de Movimiento Lineal (LMA) para preselección rápida
  - Integración orbital en potencial galáctico para refinamiento
  - Uso de Gaia DR2 como catálogo estelar

Dybczyński & Królikowska (2018):
  - Propagación de incertidumbres mediante clones orbitales
  - N-cuerpos débil para incluir perturbadores estelares

Zuluaga et al. (2018):
  - Probabilidades de origen (IOP) usando análisis bayesiano
""")
```

---

## **Pasos Siguientes (del más simple al más complejo)**

| Paso | Implementación | Complejidad | Datos Necesarios |
|------|---|---|---|
| 1️⃣ | Filtro angular por radiant + distancia actual | ⭐ | Catálogo estelar cercano |
| 2️⃣ | LMA para encuentros mínimos | ⭐⭐ | Astrometría 6D (Gaia) |
| 3️⃣ | Incertidumbres orbitales (clones) | ⭐⭐⭐ | Matriz covarianza 'Oumuamua |
| 4️⃣ | Potencial galáctico + integración | ⭐⭐⭐⭐ | Integrador ODE sofisticado |
| 5️⃣ | Probabilidades bayesianas (IOP) | ⭐⭐⭐⭐⭐ | Modelado de mecanismos eyección |

