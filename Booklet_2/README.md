# FEM 1.001 — Booklet 2

### Classification and loading on structures and mechanisms

Desarrollo técnico y computacional de los criterios de carga definidos en **FEM 1.001 — Booklet 2**, orientado al análisis estructural de equipos de izaje.

El contenido combina:

- interpretación de disposiciones normativas;
- formulación matemática;
- implementación en Python;
- tablas y gráficos de apoyo;
- aplicación a modelos estructurales de grúas.

---

## Contenido

### Cargas verticales
- Peso propio de la estructura.
- Carga de trabajo.
- Coeficiente dinámico de izaje.

### Movimientos horizontales
- Aceleración y desaceleración.
- Fuerza horizontal dinámica de la carga suspendida.
- Fuerzas de inercia de la superestructura.
- Masa equivalente de giro.
- Fuerza centrífuga.

### Efectos climáticos
- Acción del viento.
- Viento en servicio.
- Viento fuera de servicio.
- Coeficientes de forma y apantallamiento.

### Casos de carga
- **Case I:** operación sin viento.
- **Case II:** operación con viento.
- **Case III:** cargas excepcionales.

### Otras acciones
- Efectos sísmicos.
- Cargas locales sobre plataformas.
- Consideraciones especiales de FEM 1.001.

---

## Notebook

El desarrollo completo se encuentra en:

### [`FEM1001_Booklet2.ipynb`](./FEM1001_Booklet2.ipynb)

El notebook incluye las ecuaciones, comentarios técnicos, funciones Python y resultados utilizados durante el desarrollo.

---

## Flujo de trabajo

```text
FEM 1.001
    ↓
Interpretación normativa
    ↓
Formulación matemática
    ↓
Implementación en Python
    ↓
Definición de cargas
    ↓
Modelo estructural
