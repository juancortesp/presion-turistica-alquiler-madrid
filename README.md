# presion-turistica-alquiler-madrid

# Presión turística vs. precio del alquiler residencial en Madrid

## Pregunta de negocio
¿Los barrios con más pisos turísticos (Airbnb) tienen alquileres residenciales más caros,
una vez descontado el efecto de la renta, la distancia al centro y el crecimiento de población?

## Datos
| Fuente | Variable | Periodo |
|---|---|---|
| Idealista (informe de zonas) | Precio alquiler €/m² | ago-2026 |
| Inside Airbnb | Anuncios de vivienda completa | jun-2026 |
| INE | Renta media | 2023 |
| Ayuntamiento de Madrid (Panel de indicadores) | Población, viviendas, crecimiento | 2025 |

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
- La densidad de Airbnb tiene efecto positivo pero **no significativo al 5 %** (p = 0,081):
  no hay evidencia suficiente para afirmar que explique el precio por sí sola.
- Tres tipos de barrio: Centro turístico, Residencial caro, Residencial asequible.

## Limitaciones
Diseño transversal (una sola foto, no permite hablar de causalidad), relación no lineal
detectada (test RESET), 31 barrios sin precio en Idealista.

## Cómo reproducirlo
Abrir los notebooks en Google Colab en orden (01 → 04).
