# Xi_Used_Car_Price_Prediction

## Descripción del Proyecto

Rusty Bargain desea desarrollar una aplicación capaz de estimar el valor de mercado de vehículos usados a partir de sus características técnicas. El objetivo principal es construir un modelo de Machine Learning que proporcione predicciones precisas manteniendo tiempos de entrenamiento e inferencia razonables para una futura implementación en producción.

Para resolver este problema se desarrolló un flujo completo de ciencia de datos que incluyó limpieza de datos, tratamiento de valores ausentes, codificación de variables categóricas, entrenamiento de múltiples algoritmos y comparación de desempeño mediante la métrica RECM (RMSE).

---

## Objetivo de Negocio

Desarrollar un modelo predictivo capaz de estimar precios de vehículos usados con la mayor precisión posible, permitiendo:

- Publicar vehículos con precios competitivos.
- Reducir errores de valoración.
- Mejorar la experiencia de usuarios en la plataforma.
- Automatizar la estimación de precios mediante Machine Learning.

---

## Datos

El conjunto de datos contiene información sobre vehículos usados, incluyendo variables como:

- VehicleType
- RegistrationYear
- Gearbox
- Power
- Model
- Mileage
- RegistrationMonth
- FuelType
- Brand
- NotRepaired
- Price (variable objetivo)

---

## Metodología

### 1. Preparación de datos

- Exploración inicial del conjunto de datos.
- Tratamiento de valores ausentes.
- Corrección de datos inconsistentes.
- Eliminación de registros anómalos.
- Conversión de variables categóricas al tipo adecuado.

### 2. División de datos

Se dividió el conjunto de datos en:

- Entrenamiento
- Validación
- Prueba

### 3. Ingeniería de características

Para algunos modelos se utilizó:

- One-Hot Encoding (OHE)

Para LightGBM y CatBoost:

- Uso nativo de variables categóricas mediante `category`.

---

## Modelos Evaluados

### Dummy Regressor

Modelo base utilizado como referencia mínima de desempeño.

**RECM:** 4562.24

---

### Regresión Lineal

Primer modelo predictivo.

**RECM:** 2554.63

---

### Árbol de Decisión

Primer modelo no lineal evaluado.

**RECM:** 1746.37

---

### Random Forest

Ensamble de múltiples árboles de decisión.

**RECM:** 1594.89

**Tiempo aproximado:**

- 6 minutos

---

### CatBoost

Modelo de Gradient Boosting especializado en variables categóricas.

**RECM:** 1523.59

**Tiempo aproximado:**

- 13 minutos 18 segundos

---

### XGBoost

Modelo de Gradient Boosting con mecanismos avanzados de regularización.

**RECM:** 1502.43

**Tiempo aproximado:**

- 44.8 segundos

---

### LightGBM

Modelo de Gradient Boosting enfocado en escalabilidad y velocidad.

Configuración final:

```python
LGBMRegressor(
    random_state=12,
    n_estimators=2000,
    max_depth=20,
    min_samples_leaf=5,
    learning_rate=0.1
)
```

**RECM:** 1492.74

**Tiempo aproximado:**

- 25.8 segundos

---

## Comparación de Resultados

| Modelo | RECM |
|----------|----------:|
| Dummy Regressor | 4562.24 |
| Regresión Lineal | 2554.63 |
| Árbol de Decisión | 1746.37 |
| Random Forest | 1594.89 |
| CatBoost | 1523.59 |
| XGBoost | 1502.43 |
| **LightGBM** | **1492.74** |

---

## Modelo Seleccionado

### LightGBM

LightGBM fue seleccionado como el modelo final debido a que obtuvo:

- El menor RECM del proyecto.
- Excelente velocidad de entrenamiento.
- Manejo nativo de variables categóricas.
- Buena capacidad de escalabilidad.
- Excelente equilibrio entre precisión y eficiencia computacional.

---

## Conclusiones

A medida que se evaluaron modelos más complejos, la precisión mejoró de forma significativa. Los algoritmos basados en Gradient Boosting demostraron un desempeño superior frente a los modelos tradicionales.

Aunque CatBoost y XGBoost produjeron resultados altamente competitivos, LightGBM consiguió la mejor combinación entre precisión predictiva y tiempo de ejecución.

El modelo final alcanzó una raíz del error cuadrático medio de **1492.74 euros**, convirtiéndose en la alternativa más adecuada para estimar precios de vehículos usados dentro del contexto analizado.

---

## Tecnologías Utilizadas

- Python
- Pandas
- NumPy
- Scikit-Learn
- LightGBM
- CatBoost
- XGBoost
- Matplotlib
- Seaborn
- Jupyter Notebook

---

## Autor

**Santiago Rodríguez Zaraza**

Proyecto Xi - Portafolio de Ciencia de Datos
