# 🤖 Telecom X — Parte 2: Predicción de Cancelación de Clientes

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.0%2B-F7931E?logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Completado-brightgreen)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?logo=googlecolab)

---

## 📌 ¿De qué trata este proyecto?

En la **Parte 1** descubrimos *qué* tipos de clientes se van de Telecom X.
En esta **Parte 2** construimos un modelo que puede *predecir* qué cliente
se va a ir **antes de que suceda**, para que la empresa pueda actuar a tiempo.

> 🎯 **Objetivo:** Predecir qué clientes cancelarán el servicio usando
> Machine Learning, e identificar los factores que más influyen en esa decisión.

---

## 📊 El problema en números

| Dato | Valor |
|---|---|
| 👥 Clientes analizados | ~7.000 |
| ❌ Tasa de cancelación | ~26% |
| ✅ Tasa de retención | ~74% |
| ⚖️ Desbalance de clases | Moderado — tratado con SMOTE |

---

## 🔄 ¿Qué pasos seguimos?

```
1. Cargar el dataset limpio de la Parte 1
        ↓
2. Eliminar columnas que no aportan al modelo
        ↓
3. Convertir texto a números (Encoding)
        ↓
4. Balancear las clases con SMOTE
        ↓
5. Normalizar los datos numéricos
        ↓
6. Analizar correlaciones entre variables
        ↓
7. Dividir datos en entrenamiento (70%) y prueba (30%)
        ↓
8. Entrenar 2 modelos de predicción
        ↓
9. Evaluar y comparar los modelos
        ↓
10. Identificar qué variables importan más
        ↓
11. Conclusiones y recomendaciones estratégicas
```

---

## 🤖 Modelos utilizados

### 📈 Regresión Logística
- Modelo matemático simple y muy interpretable
- **Requiere** que los datos estén en la misma escala
- Sus coeficientes nos dicen exactamente qué variables
  aumentan o reducen el riesgo de cancelación

### 🌲 Random Forest
- Conjunto de cientos de árboles de decisión trabajando juntos
- **No requiere** escalar los datos
- Muy bueno detectando patrones complejos
- Nos dice cuáles variables son más importantes para predecir

---

## ⚙️ Técnicas de preprocesamiento

| Técnica | ¿Para qué sirve? | ¿Se aplicó? |
|---|---|---|
| **Label Encoding** | Convertir Sí/No → 1/0 | ✅ |
| **One-Hot Encoding** | Convertir categorías en columnas | ✅ |
| **SMOTE** | Balancear clientes que se van vs los que se quedan | ✅ |
| **StandardScaler** | Poner todas las variables en la misma escala | ✅ Solo para Reg. Logística |
| **Train/Test Split** | Separar datos para entrenar y evaluar | ✅ 70% / 30% |

### ¿Por qué SMOTE?
El dataset tiene ~74% de clientes que se quedan y solo ~26% que se van.
Si entrenamos el modelo así, aprende a decir siempre "se queda" y parece
preciso pero es inútil. SMOTE genera ejemplos sintéticos del grupo minoritario
para que el modelo aprenda a detectar ambos casos por igual.

---

## 📏 ¿Cómo medimos si el modelo es bueno?

Para este problema **no basta con la Accuracy** (exactitud). Lo que más
importa es el **Recall**: detectar la mayor cantidad posible de clientes
que se van a ir, aunque a veces nos equivoquemos.

| Métrica | ¿Qué mide? | ¿Por qué importa? |
|---|---|---|
| **Accuracy** | % de predicciones correctas | Referencia general |
| **Precision** | De los que predijo "se va", ¿cuántos realmente se fueron? | Evitar falsas alarmas |
| **Recall** | De los que se fueron, ¿cuántos detectó? | ⭐ La más importante aquí |
| **F1-Score** | Balance entre Precision y Recall | Métrica principal |
| **ROC-AUC** | Capacidad general de distinguir entre clases | Rendimiento global |

---

## 🏆 Resultados

| Métrica | Regresión Logística | Random Forest |
|---|---|---|
| Accuracy | — | — |
| Precision | — | — |
| Recall | — | — |
| F1-Score | — | — |
| ROC-AUC | — | — |

> 📌 Los valores exactos se encuentran en el notebook tras ejecutarlo.

---

## 🔑 Factores que más influyen en la cancelación

Basado en ambos modelos, estos son los factores que más predicen si un cliente se va:

### 🔴 Factores de riesgo (aumentan la cancelación)
- 📅 **Poca antigüedad** — los clientes nuevos se van más fácilmente
- 💰 **Cargo mensual alto** — a mayor costo, mayor probabilidad de irse
- 📄 **Contrato mes a mes** — sin compromiso a largo plazo
- 💳 **Pago por cheque electrónico** — menor vínculo con la empresa

### 🟢 Factores de protección (reducen la cancelación)
- 📋 **Contratos anuales o bianuales** — compromiso a largo plazo
- 🔒 **Múltiples servicios contratados** — mayor vinculación
- 🛡️ **Servicios adicionales activos** — seguridad, soporte, backup

---

## 🚀 Recomendaciones estratégicas

1. **Intervención temprana** — contactar a clientes nuevos en los primeros 3 meses
2. **Scoring mensual** — ejecutar el modelo sobre todos los clientes activos
3. **Alertas de riesgo** — notificar al equipo comercial cuando un cliente supera el 60% de probabilidad de cancelar
4. **Incentivar contratos largos** — descuentos por comprometerse a 1 o 2 años
5. **Revisión de precios** — planes personalizados para clientes con cargos altos en riesgo

---

## 🛠️ Tecnologías utilizadas

| Librería | Uso |
|---|---|
| `Pandas` | Manipulación de datos |
| `NumPy` | Operaciones numéricas |
| `Scikit-learn` | Modelos ML y métricas |
| `Imbalanced-learn` | SMOTE para balanceo de clases |
| `Matplotlib` | Visualizaciones |
| `Seaborn` | Gráficas estadísticas |
| `IPython` | Renderizado del informe en Markdown |

---

## 📁 Estructura del repositorio

```
telecomx-churn-ml/
│
├── TelecomX_Parte2.ipynb       # Notebook principal con todo el pipeline
├── telecomx_limpio.csv         # Dataset limpio exportado de la Parte 1
└── README.md                   # Este archivo
```

---

## ▶️ Cómo ejecutar el proyecto

1. Abre el notebook en **Google Colab**

   [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

2. Sube el archivo `telecomx_limpio.csv` cuando el notebook lo solicite

3. Ejecuta las celdas en orden — cada sección está documentada

4. No se requieren instalaciones adicionales excepto `imbalanced-learn`,
   que se instala automáticamente en la primera celda

---

## 🔗 Relación con la Parte 1

Este repositorio es la continuación directa del análisis exploratorio:

| Parte | Contenido |
|---|---|
| [📊 Parte 1](../telecomx-churn-analysis) | Limpieza, exploración y visualización de datos |
| [🤖 Parte 2](.) | Modelado predictivo con Machine Learning |

---

## 👤 Autor

Hugo Rodríguez. Proyecto desarrollado como parte del **Challenge 2 — Data Science LATAM**

---

## 📄 Licencia

Proyecto de uso educativo desarrollado con fines de aprendizaje en Data Science y Machine Learning.
