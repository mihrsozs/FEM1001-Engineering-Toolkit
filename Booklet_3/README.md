# FEM 1.001 – Booklet 3

## Calculating the Stresses in Structures

Implementación en Python de procedimientos de evaluación estructural basados en **FEM 1.001 – Booklet 3**, orientada a automatizar verificaciones de elementos estructurales de equipos de izaje.

Este módulo forma parte del repositorio:

**FEM1001-Engineering-Toolkit**

y continúa el flujo desarrollado en `Booklet_2`, utilizando las cargas y casos definidos previamente para evaluar posteriormente la respuesta estructural.

---

## Contenido

El Booklet 3 aborda la evaluación resistente de los elementos estructurales de la grúa, incluyendo:

- selección y propiedades del acero;
- verificación respecto al límite elástico;
- tensiones normales y de corte;
- estados combinados de tensión;
- crippling;
- buckling;
- deformaciones significativas;
- verificación por fatiga.

El desarrollo del notebook se estructura progresivamente siguiendo la organización de FEM 1.001.

---

## Notebook

El desarrollo principal se encuentra en:

[`FEM1001_Booklet3v2.ipynb`](./FEM1001_Booklet3v2.ipynb)

El notebook combina:

- interpretación del procedimiento FEM;
- formulación matemática;
- implementación mediante funciones de Python;
- clasificación automática de casos;
- cálculo de tensiones admisibles;
- evaluación mediante factores de utilización.

---

## Verificación elástica

La verificación elástica utiliza las propiedades mecánicas del material:

- `fy`: límite elástico;
- `fu`: resistencia última;
- `Case I`;
- `Case II`;
- `Case III`.

Para aceros con:

$$
\frac{f_y}{f_u}<0.70
$$

la tensión admisible se determina mediante:

$$
\sigma_a=\frac{f_y}{\nu_E}
$$

con:

$$
\nu_E=
\begin{cases}
1.50 & \text{Case I}\\
1.33 & \text{Case II}\\
1.10 & \text{Case III}
\end{cases}
$$

La tensión admisible a corte corresponde a:

$$
\tau_a=\frac{\sigma_a}{\sqrt{3}}
$$

Para estados planos de tensión se verifica además:

$$
\sigma_{cp}=\sqrt{\sigma_x^2+\sigma_y^2-\sigma_x\sigma_y+3\tau_{xy}^2}
$$

debiendo cumplirse:

$$
\sigma_{cp}\leq\sigma_a
$$

También deben verificarse individualmente:

$$
|\sigma_x|\leq\sigma_a
$$

$$
|\sigma_y|\leq\sigma_a
$$

$$
|\tau_{xy}|\leq\tau_a
$$

---

## Verificación por fatiga

La evaluación por fatiga se desarrolla a partir de la historia local de tensiones del componente estructural.

El procedimiento general implementado es:

$$
n\rightarrow B
$$

$$
k_{sp}\rightarrow P
$$

$$
B+P\rightarrow E
$$

$$
E+W/K\rightarrow\sigma_W
$$

$$
\sigma_{\max},\sigma_{\min}\rightarrow\kappa
$$

$$
\sigma_W+\kappa\rightarrow\sigma_{adm,\;fatiga}
$$

donde:

- `B`: clase de utilización del componente;
- `P`: clase del espectro de tensiones;
- `E`: grupo de clasificación del componente;
- `W0-W2`: categorías para detalles no soldados;
- `K0-K4`: categorías para detalles soldados;
- `σW`: resistencia base de fatiga;
- `κ`: relación entre tensiones extremas.

---

## Historias de tensión

Para elementos tipo shell, la evaluación se plantea utilizando las componentes locales:

$$
S11(t)
$$

$$
S22(t)
$$

$$
S12(t)
$$

manteniendo la correspondencia con:

- elemento;
- nodo del elemento;
- cara `Top` o `Bottom`;
- estado operacional de la grúa.

La unidad básica de evaluación puede representarse como:

```text
AreaElem + Joint + Face
