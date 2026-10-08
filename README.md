# Presión turística vs. precio del alquiler residencial en Madrid

![Portada](img/portada.png)

> **Conclusión:** no hay evidencia suficiente de que los pisos turísticos encarezcan el alquiler. Lo que explica el precio es la **renta del barrio** y la **distancia al centro**.

📄 [Ver portfolio en PDF](https://github.com/juancortesp/portfolio) · 📊 [Dashboard Power BI](dashboard/)

## Pregunta de negocio
¿Los barrios con más pisos turísticos (Airbnb) tienen alquileres residenciales más caros, una vez descontado el efecto de la renta, la distancia al centro y el crecimiento de población?

## Datos
| Fuente | Variable | Periodo |
|---|---|---|
| Idealista (informe de zonas) | Precio alquiler €/m² | ago-2026 |
| Inside Airbnb | Anuncios de vivienda completa | jun-2026 |
| INE | Renta media | 2023 |
| Ayuntamiento de Madrid (Panel de indicadores) | Población, viviendas, crecimiento | 2025 |
| Callejero oficial | Polígonos de los 131 barrios | GeoJSON |

Unidad de análisis: barrio (100 de los 131 oficiales con precio disponible).

## Metodología
1. Limpieza y unión de fuentes por código de barrio → `01_limpieza_y_merge.ipynb`
2. Análisis exploratorio, outliers y multicolinealidad (VIF) → `02_eda.ipynb`
3. Regresión lineal múltiple (OLS) → `03_regresion_lineal.ipynb`
4. Segmentación de barrios con K-means → `04_clustering.ipynb`
5. Dashboard en Power BI → `dashboard/`

## Resultados principales
- El modelo explica el 70 % de las diferencias de precio entre barrios (R² = 0,70).
- Renta, distancia al centro y crecimiento de población son significativos.
- La densidad de Airbnb tiene efecto positivo pero **no significativo al 5 %** (p = 0,081): no hay evidencia suficiente para afirmar que explique el precio por sí sola.
- Tres tipos de barrio: Centro turístico, Residencial caro, Residencial asequible.

### En cifras
| Indicador | Valor |
|---|---|
| Alquiler medio, piso de 70 m² | 1.483 €/mes |
| Barrios donde un piso de 100 m² supera el 30 % de la renta | 91 de cada 100 |
| Anuncios de Airbnb concentrados en el distrito Centro | 43 % |
| Peso máximo de los pisos turísticos sobre el alquiler | 2,2 % (0–31 €/mes) |

## Dashboard
![Resultados](img/resultados.png)
![Variables que explican el precio](img/variables.png)

## Limitaciones
- Diseño transversal: muestra asociación, no causalidad.
- El test RESET detecta no linealidad, lo que abre la puerta a modelos no lineales en una siguiente versión.
- 31 barrios sin precio publicado quedan fuera del modelo.

## Stack
Python (pandas, NumPy, GeoPandas, statsmodels, scikit-learn, matplotlib, seaborn) · Jupyter / Google Colab · Power BI · Git

## Cómo ejecutarlo
Abre los notebooks en orden (01 → 04) en Jupyter o Google Colab.

---
**Juan Cortés** · Data Analyst · [LinkedIn](https://www.linkedin.com/in/juan-cortes-paredes/) · infojuancortesp@gmail.com
