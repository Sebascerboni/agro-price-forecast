# Agro Price Forecast Platform

Sistema de predicción de precios agrícolas basado en Inteligencia Artificial y Series Temporales para productos agrícolas del Ecuador.

---

## Objetivo

Desarrollar una plataforma que permita analizar y predecir precios agrícolas utilizando diferentes enfoques de modelado:

* ARIMA / SARIMAX
* LSTM
* XGBoost

La plataforma permite comparar el desempeño de cada modelo y visualizar tendencias futuras de precios por producto y provincia.

---

# Arquitectura

```text
agro-price-forecast/
│
├── apps/
│   ├── api/
│   └── web/
│
├── docker-compose.yml
├── .env.example
└── README.md
```

---

# Backend

Tecnologías:

* Python 3.11
* FastAPI
* Uvicorn
* TensorFlow
* XGBoost
* Statsmodels
* Pandas
* NumPy
* Scikit-Learn

Responsabilidades:

* Carga de modelos entrenados
* Predicciones
* Comparación de modelos
* Métricas de desempeño
* Exposición de API REST

---

# Frontend

Tecnologías:

* React
* TypeScript
* Vite
* Axios
* Recharts
* i18next
* react-i18next

Responsabilidades:

* Visualización de resultados
* Comparación de modelos
* Dashboard analítico
* Interpretación de predicciones

---

# Productos Disponibles

Actualmente el sistema soporta:

* Maracuyá
* Papa Superchola
* Tomate Riñón de Invernadero

---

# Modelos Implementados

## ARIMA / SARIMAX

Modelo estadístico especializado en series temporales.

Características:

* Entrenamiento por provincia.
* Pronóstico basado en comportamiento histórico.

---

## LSTM

Red neuronal recurrente para series temporales.

Características:

* Ventanas temporales.
* Variables agrícolas.
* Variables macroeconómicas.
* Variables temporales.

---

## XGBoost

Modelo Gradient Boosting para regresión.

Características:

* Variables históricas.
* Variables económicas.
* Variables de producción agrícola.
* Variables de fertilizantes.

---

# API Endpoints

## Productos disponibles

```http
GET /products
```

---

## Resumen del producto

```http
GET /products/{product_id}/summary
```

Incluye:

* Provincias disponibles
* Modelos disponibles
* Métricas históricas

---

## Predicción individual

```http
POST /predict
```

```json
{
  "product_id": "papa_superchola",
  "model_name": "xgboost",
  "province": "Pichincha",
  "horizon": 3
}
```

---

## Comparación de modelos

```http
POST /predict/compare
```

```json
{
  "product_id": "papa_superchola",
  "province": "Pichincha",
  "horizon": 3
}
```

Respuesta:

* Histórico reciente
* Predicciones
* Mejor modelo
* Variación porcentual
* Interpretación automática

---

# Desarrollo Local

## Backend

```bash
cd apps/api

python -m venv .venv

source .venv/bin/activate

pip install -r requirements.txt

uvicorn app.main:app --reload
```

Swagger:

```text
http://localhost:8000/docs
```

---

## Frontend

```bash
cd apps/web

npm install

npm run dev
```

Aplicación:

```text
http://localhost:5173
```

---

# Docker

Levantar todo el entorno:

```bash
docker compose up --build
```

Frontend:

```text
http://localhost:5173
```

Backend:

```text
http://localhost:8000
```

Swagger:

```text
http://localhost:8000/docs
```

---

# Variables de Entorno

Backend:

```env
ALLOWED_ORIGINS=http://localhost:5173
```

Frontend:

```env
VITE_API_URL=http://localhost:8000
```

---

# Funcionalidades

* Predicción de precios agrícolas
* Comparación de modelos
* Visualización histórica
* Dashboard analítico
* Métricas de desempeño
* Interpretación automática de tendencias
* Internacionalización (i18n)
* Arquitectura desacoplada API/Web
* Despliegue mediante Docker

---

# Objetivo Académico

Este proyecto forma parte de una investigación de Maestría orientada al análisis predictivo de precios agrícolas mediante técnicas de Inteligencia Artificial y Aprendizaje Automático, aplicadas al contexto productivo ecuatoriano.
