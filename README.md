# 📊 TelecomX - Análisis de Evasión de Clientes (Customer Churn)

## 📋 Descripción del Proyecto

Este proyecto forma parte del análisis de **Customer Churn (Evasión de Clientes)** para TelecomX, una empresa de telecomunicaciones que enfrenta una alta tasa de cancelaciones. El objetivo es identificar los factores que contribuyen a la pérdida de clientes y desarrollar estrategias de retención basadas en datos.

### 🎯 Objetivos

- **Primario**: Identificar patrones y factores que influyen en la evasión de clientes
- **Secundario**: Proporcionar insights accionables para estrategias de retención
- **Terciario**: Establecer una base de datos limpia para futuros modelos predictivos

## 🗂️ Estructura del Proyecto

```
TelecomX-Churn-Analysis/
│
├── data/
│   └── TelecomX_Data.json          # Datos originales (API)
│
├── notebooks/
│   └── TelecomX.ipynb              # Notebook principal con análisis
│
├── src/
│   ├── data_processing.py          # Funciones de limpieza de datos
│   ├── visualization.py            # Funciones de visualización
│   └── analysis.py                 # Funciones de análisis estadístico
│
├── reports/
│   ├── informe_final.md            # Informe ejecutivo completo
│   └── visualizations/             # Gráficos y visualizaciones
│
├── requirements.txt                # Dependencias del proyecto
└── README.md                       # Este archivo
```

## 🛠️ Tecnologías Utilizadas

### Lenguajes y Librerías Principales
- **Python 3.8+**: Lenguaje de programación principal
- **Pandas**: Manipulación y análisis de datos
- **NumPy**: Computación numérica
- **Matplotlib**: Visualización de datos
- **Seaborn**: Visualización estadística avanzada

### Herramientas de Desarrollo
- **Google Colaboratory**: Desarrollo interactivo
- **Git**: Control de versiones
- **JSON**: Formato de datos de entrada

## 📊 Dataset

### Fuente de Datos
```
API URL: https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/main/TelecomX_Data.json
```

### Estructura de Datos Original
Los datos están organizados en formato JSON anidado con las siguientes secciones:

```json
{
  "customerID": "string",
  "customer": {
    "gender": "string",
    "Partner": "string",
    "Dependents": "string"
  },
  "phone": {
    "PhoneService": "string",
    "MultipleLines": "string"
  },
  "internet": {
    "InternetService": "string",
    "OnlineBackup": "string",
    "DeviceProtection": "string",
    "TechSupport": "string"
  },
  "account": {
    "Contract": "string",
    "PaperlessBilling": "string",
    "PaymentMethod": "string",
    "tenure": "integer",
    "Charges": {
      "Monthly": "float",
      "Total": "string"
    }
  },
  "Churn": "string"
}
```

### Variables Procesadas

#### Variables Demográficas
- `customerID`: Identificador único del cliente
- `gender`: Género del cliente (0: Male, 1: Female)
- `Partner`: Tiene pareja (0: No, 1: Yes)
- `Dependents`: Tiene dependientes (0: No, 1: Yes)

#### Variables de Servicios
- `PhoneService`: Servicio telefónico (0: No, 1: Yes)
- `MultipleLines`: Múltiples líneas telefónicas
- `InternetService`: Tipo de servicio de internet
- `OnlineBackup`: Servicio de backup online
- `DeviceProtection`: Protección de dispositivos
- `TechSupport`: Soporte técnico

#### Variables de Cuenta
- `Contract`: Tipo de contrato (Month-to-month, One year, Two year)
- `PaperlessBilling`: Facturación sin papel (0: No, 1: Yes)
- `PaymentMethod`: Método de pago
- `tenure`: Tiempo como cliente (en meses)
- `Charges.Monthly`: Cargo mensual
- `Charges.Total`: Cargo total
- `Cuentas_Diarias`: Cargo diario calculado (Monthly/30)

#### Variable Objetivo
- `Churn`: Evasión del cliente (0: No, 1: Yes)

## 🚀 Instalación y Configuración

### 1. Guardar el Repositoria
Se guarda directamente desde Google Colaboratory

### 2. Crear Entorno Virtual
El entorno virtual es Google Colaboratory


## 📈 Análisis Realizado

### 1. Extracción y Carga de Datos
- Conexión directa a API externa
- Carga de datos JSON en formato DataFrame
- Normalización de datos anidados

### 2. Limpieza y Preprocesamiento
- **Detección de inconsistencias**: Valores ausentes y tipos incorrectos
- **Transformación de variables**: Conversión de categóricas a numéricas
- **Creación de variables derivadas**: Cálculo de cuentas diarias
- **Validación de datos**: Verificación de duplicados y valores atípicos

### 3. Análisis Exploratorio de Datos (EDA)
- **Distribución de evasión**: Análisis de la variable objetivo
- **Análisis univariado**: Distribución de variables individuales
- **Análisis bivariado**: Relación entre variables y evasión
- **Correlaciones**: Matriz de correlación entre variables numéricas

### 4. Visualizaciones Implementadas
- Gráficos de barras para distribución de evasión
- Gráficos de pastel para proporciones
- Boxplots para variables numéricas
- Heatmap de correlaciones
- Análisis categórico por grupos

## 📊 Principales Hallazgos

### Tasa de Evasión General
- **26.5%** de los clientes abandonan el servicio
- **73.5%** de los clientes permanecen
- Tasa considerada **crítica** para el sector

### Factores de Mayor Impacto

#### 🔴 Alto Riesgo de Evasión
- **Contratos mes a mes**: Mayor flexibilidad = mayor evasión
- **Nuevos clientes**: Primeros 12 meses críticos
- **Facturas altas sin servicios adicionales**: Percepción de bajo valor
- **Sin pareja/dependientes**: Menor estabilidad

#### 🟢 Factores de Retención
- **Contratos anuales/bianuales**: Mayor compromiso
- **Servicios complementarios**: Mayor valor percibido
- **Clientes antiguos**: Mayor lealtad
- **Métodos de pago estables**: Tarjetas vs cheques electrónicos

### Correlaciones Clave
- **Tenure vs Churn**: Correlación negativa fuerte (-0.35)
- **Monthly Charges vs Churn**: Correlación positiva moderada (+0.19)
- **Contract Type**: Impacto significativo en retención

## 🎯 Recomendaciones sugeridas

### Estrategias de Retención

#### 1. **Programa de Onboarding Intensivo**
- Seguimiento personalizado primeros 12 meses
- Descuentos progresivos para nuevos clientes
- KPI: Reducir evasión nuevos clientes del 35% al 20%

#### 2. **Optimización Contractual**
- Incentivos para contratos anuales (10-15% descuento)
- Planes híbridos de 6 meses como opción intermedia
- KPI: Incrementar contratos anuales del 25% al 45%

#### 3. **Bundling Inteligente**
- Paquetes atractivos con servicios complementarios
- Ofertas familiares para clientes con dependientes
- KPI: Aumentar penetración servicios del 30% al 55%

## 🔧 Uso del Código

### Ejecutar Análisis Completo
```python
# Importar librerías
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Cargar datos
api_url = "https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/main/TelecomX_Data.json"
df_telecom = pd.read_json(api_url)

# Procesar datos
from src.data_processing import process_telecom_data
df_clean = process_telecom_data(df_telecom)

# Generar visualizaciones
from src.visualization import create_churn_visualizations
create_churn_visualizations(df_clean)

# Análisis estadístico
from src.analysis import analyze_churn_factors
results = analyze_churn_factors(df_clean)
```

## 📈 Métricas de Éxito

### KPIs Definidos
- **Tasa de Evasión General**: Objetivo 26.5% → 18%
- **Retención Primeros 12 Meses**: Objetivo 65% → 80%
- **Valor de Vida del Cliente**: Incremento 25%
- **ROI Programas Retención**: Mínimo 3:1

### Monitoreo
- Dashboards en tiempo real
- Reportes mensuales automatizados
- Análisis trimestral de efectividad
- Revisión anual de estrategias

## 📝 Próximos Pasos

### Fase 2: Modelado Predictivo
- [ ] Implementar modelos de Machine Learning
- [ ] Random Forest para predicción de churn
- [ ] Logistic Regression para interpretabilidad
- [ ] XGBoost para máxima precisión

### Fase 3: Implementación Operacional
- [ ] API para predicciones en tiempo real
- [ ] Dashboard interactivo con Streamlit/Dash
- [ ] Sistema de alertas automáticas
- [ ] Integración con CRM existente

### Fase 4: Optimización Continua
- [ ] A/B Testing de estrategias de retención
- [ ] Análisis de cohortes longitudinal
- [ ] Segmentación avanzada con clustering
- [ ] Optimización de campañas de marketing

## 👥 Equipo del Proyecto

- **Analista de Datos**: Desarrollo del análisis exploratorio
- **Data Scientist**: Modelado y predicciones
- **Business Analyst**: Interpretación y recomendaciones
- **Project Manager**: Coordinación y seguimiento

## 📞 Contacto y Soporte

Para preguntas, sugerencias o reportar problemas:

- **Email**: belgomez8@gmail.com

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo `LICENSE` para más detalles.

## 🙏 Agradecimientos

- **TelecomX**: Por proporcionar los datos y el caso de estudio
- **LATAM Data Science Challenge**: Por la estructura del dataset
- **Comunidad Python**: Por las herramientas y librerías utilizadas

---

**Última actualización**: Julio 2025  
**Versión**: 1.0.0  
**Estado**: Completado - En fase de implementación

---

### 📊 Visualización Rápida de Resultados

```python
# Código para generar resumen ejecutivo rápido
import pandas as pd

# Métricas clave
metricas = {
    'Tasa de Evasión Actual': '26.5%',
    'Objetivo Tasa de Evasión': '18.0%',
    'Clientes Analizados': '7,043',
    'Factores de Riesgo Identificados': '12',
    'ROI Esperado': '300%',
    'Tiempo de Implementación': '6 meses'
}

for metrica, valor in metricas.items():
    print(f"📊 {metrica}: {valor}")
```

**¡Gracias por contribuir al éxito de TelecomX! 🚀**
