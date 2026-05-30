# 📱 Megaline Plan Recommender

![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=flat&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.8-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-26b56e?style=flat)
![Accuracy](https://img.shields.io/badge/Accuracy-81.8%25-1a5c38?style=flat)

---

## El problema

Megaline, una operadora móvil, tiene miles de clientes activos en planes heredados que ya no reflejan su comportamiento de uso real. El equipo comercial necesita una herramienta que identifique automáticamente qué plan — **Smart** o **Ultra** — es el más adecuado para cada cliente, basándose en su historial mensual de llamadas, minutos, mensajes y consumo de datos.

Este proyecto construye ese modelo de clasificación desde cero: desde el análisis exploratorio hasta la evaluación final en producción.

---

## Resultados

| Modelo | Accuracy Validación | Accuracy Test | Supera umbral 0.75 |
|--------|--------------------|--------------|--------------------|
| **Random Forest** | **0.7963** | **0.8180** | ✅ |
| Decision Tree | 0.7900 | — | ✅ |
| Logistic Regression | 0.7449 | — | ❌ |

**Mejora sobre baseline trivial:** +12.44 puntos porcentuales

---

## Hallazgos clave

- **`mb_used` es la variable más predictiva (37.3%)** — el consumo de datos supera en importancia a las llamadas y mensajes combinados para identificar usuarios Ultra.
- **La Regresión Logística no supera el umbral** — confirma que las relaciones entre comportamiento de uso y tipo de plan no son lineales.
- **Random Forest generaliza bien** — gap de solo 0.054 entre train y validación, sin señales de overfitting severo.
- **El desbalance de clases (69% Smart / 31% Ultra)** no comprometió el modelo gracias al split estratificado.

---

## Estructura del proyecto

```
megaline-plan-recommender/
├── megaline_plan_recommender.ipynb   # Notebook principal
├── users_behavior.csv                # Dataset
└── README.md
```

---

## Estructura del notebook

| Sección | Contenido |
|---------|-----------|
| 1 | Carga e inspección inicial |
| 2 | Análisis exploratorio — estadísticas, distribuciones, correlaciones |
| 3 | Visualizaciones — histogramas, boxplots, heatmap |
| 4 | Segmentación 60/20/20 con stratify |
| 5 | Entrenamiento — Decision Tree, Random Forest, Logistic Regression |
| 6 | Comparación de modelos |
| 7 | Evaluación final en test — matriz de confusión, feature importance |
| 8 | Prueba de cordura vs baselines triviales |
| 9 | Conclusiones y recomendaciones de negocio |

---

## Stack técnico

- **Python 3.11**
- **pandas** — manipulación de datos
- **numpy** — operaciones numéricas
- **matplotlib / seaborn** — visualizaciones
- **scikit-learn** — modelos, métricas, pipelines

---

## Cómo reproducir

```bash
git clone https://github.com/he1109-ci3l0/megaline-plan-recommender
cd megaline-plan-recommender
pip install pandas numpy matplotlib seaborn scikit-learn
jupyter notebook megaline_plan_recommender.ipynb
```

---

## Sobre este proyecto

Desarrollado como proyecto final del Sprint 10 — Introducción a Machine Learning en el programa de Data Science de TripleTen.

**Autor:** ci3l0 · [GitHub](https://github.com/he1109-ci3l0)
