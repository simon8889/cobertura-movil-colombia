# 📡 Análisis y Predicción de Cobertura Móvil en Colombia

> Proyecto completo de ciencia de datos que analiza la evolución histórica de la cobertura móvil por tecnología (2G, 3G, 4G, LTE, 5G) en Colombia y predice la expansión futura de 5G hasta 2028.

[![Python](https://img.shields.io/badge/Python-3.12-blue.svg)](https://python.org)
[![Pandas](https://img.shields.io/badge/Pandas-2.0+-green.svg)](https://pandas.pydata.org)
[![Plotly](https://img.shields.io/badge/Plotly-6.0+-orange.svg)](https://plotly.com)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.7+-red.svg)](https://scikit-learn.org)

---

## 📋 Tabla de Contenidos

- [Descripción del Proyecto](#-descripción-del-proyecto)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Fuentes de Datos](#-fuentes-de-datos)
- [Análisis Realizados](#-análisis-realizados)
- [Modelo de Machine Learning](#-modelo-de-machine-learning)
- [Visualizaciones](#-visualizaciones)
- [Instalación y Uso](#-instalación-y-uso)
- [Resultados Principales](#-resultados-principales)
- [Documentación Adicional](#-documentación-adicional)

---

## 🎯 Descripción del Proyecto

Este proyecto realiza un **análisis exhaustivo de la infraestructura de telecomunicaciones móviles en Colombia**, abarcando desde el año 2015 hasta 2023, con datos de:

- **407,280 registros** de cobertura móvil
- **33 departamentos** y **1,037 municipios**
- **8 proveedores** de telecomunicaciones
- **6 generaciones tecnológicas**: 2G, 3G, HSPA+, 4G, LTE y 5G

### Objetivos Principales

1. **Analizar la evolución histórica** de la cobertura móvil en Colombia
2. **Visualizar patrones geográficos** de distribución de tecnologías
3. **Identificar brechas digitales** y oportunidades de expansión
4. **Predecir el crecimiento de 5G** para los años 2025-2028
5. **Proporcionar insights** para toma de decisiones estratégicas

---

## 📁 Estructura del Proyecto

```
findal-ds/
│
├── data/                                    # Datasets
│   ├── cobertura_movil_con_datos_geograficos.csv  # Dataset principal (407k registros)
│   ├── Cobertura_móvil_por_tecnología...csv       # Datos originales
│   └── DIVIPOLA_CentrosPoblados.csv               # Coordenadas geográficas
│
├── graficos/                                # Visualizaciones HTML interactivas (16 archivos)
│   ├── crecimiento_cobertura_movil_por_tecnologia.html
│   ├── mapa_cobertura_4g_municipios.html
│   ├── prediccion_5g_nacional.html
│   └── ...
│
├── exploracion_de_datos.ipynb              # Análisis exploratorio y visualizaciones
├── prediccion_expansion_cobertura.ipynb    # Modelo ML de predicción 5G
│
├── README.md                                # Este archivo
├── MODELO_ML.md                            # Documentación detallada del modelo
├── requirements.txt                         # Dependencias Python
└── venv/                                   # Entorno virtual
```

---

## 📊 Fuentes de Datos

### Dataset Principal
- **Nombre**: `cobertura_movil_con_datos_geograficos.csv`
- **Tamaño**: 407,280 registros × 25 columnas
- **Período**: 2015-2023 (9 años)
- **Granularidad**: Trimestral por centro poblado

### Columnas Principales

| Columna | Descripción | Tipo |
|---------|-------------|------|
| `AÑO` | Año del registro (2015-2023) | Entero |
| `TRIMESTRE` | Trimestre del año (1-4) | Entero |
| `PROVEEDOR` | Operador móvil (8 únicos) | Texto |
| `DEPARTAMENTO` | Departamento (33 únicos) | Texto |
| `MUNICIPIO` | Municipio (1,037 únicos) | Texto |
| `CENTRO POBLADO` | Centro poblado específico | Texto |
| `COBERTURA 2G/3G/4G/LTE/5G` | Cobertura por tecnología (S/N) | Booleano |
| `Latitud` | Coordenada geográfica | Float |
| `Longitud` | Coordenada geográfica | Float |

### Proveedores Analizados

1. COLOMBIA MOVIL S.A ESP (Tigo)
2. COMUNICACION CELULAR S A COMCEL S A (Claro)
3. COLOMBIA TELECOMUNICACIONES S.A. E.S.P. (Movistar)
4. PARTNERS TELECOM COLOMBIA SAS (WOM)
5. AVANTEL S.A.S
6. EMPRESA DE TELECOMUNICACIONES DE BOGOTA S.A. ESP (ETB)
7. ALMACENES EXITO INVERSIONES S.A.S.
8. UNE EPM TELECOMUNICACIONES S.A.

---

## 🔍 Análisis Realizados

### 1. Exploración de Datos (`exploracion_de_datos.ipynb`)

#### Análisis Temporal
- **Crecimiento de cobertura** por tecnología (2015-2023)
- **Evolución de cuota de mercado** por proveedor
- **Velocidad de adopción** de nuevas tecnologías
- **Identificación de líderes** por tecnología y región

#### Análisis Geográfico
- **Distribución espacial** de cobertura por tecnología
- **Densidad de cobertura** 4G por departamento
- **Brechas digitales** (zonas sin cobertura)
- **Penetración de LTE** sobre 4G básico
- **Comparación entre proveedores** por región

#### Funciones Clave Implementadas

```python
def analizar_cuota_mercado_por_tecnologia(df, tecnologia, año):
    """
    Calcula la cuota de mercado de cada proveedor para una tecnología específica.
    
    Returns:
        DataFrame con columnas: PROVEEDOR, Centros con cobertura, Porcentaje
    """
    
def analizar_evolucion_cuota_mercado(df, tecnologia):
    """
    Analiza la evolución temporal de la cuota de mercado.
    
    Returns:
        DataFrame con series temporales por proveedor
    """
```

### 2. Visualizaciones Geográficas

Se generaron **6 mapas interactivos** usando Plotly con OpenStreetMap:

1. **Cobertura 4G por municipio** - Visualiza puntos de cobertura con tamaño proporcional
2. **Proveedores Top 4** - Compara distribución geográfica entre operadores
3. **Distribución de tecnologías** - Muestra mejor tecnología disponible por zona
4. **Brechas de cobertura** - Identifica municipios sin cobertura 4G
5. **Penetración LTE** - % de LTE sobre total 4G por departamento
6. **Centros por departamento** - Densidad de centros poblados

**Características de los mapas:**
- Interactividad completa (zoom, pan, hover)
- Burbujas con tamaño proporcional a datos
- Código de colores por categoría
- Tooltips con información detallada
- Exportables como imágenes estáticas

---

## 🤖 Modelo de Machine Learning

### Objetivo
**Predecir la expansión de cobertura 5G en Colombia para los años 2025-2028**

### Metodología

#### Enfoque: Análisis de Curvas de Adopción
El modelo se basa en que las tecnologías móviles siguen patrones de adopción similares (curva S):

1. **Introducción** → Crecimiento lento inicial
2. **Expansión** → Aceleración exponencial  
3. **Madurez** → Saturación del mercado
4. **Declive** → Reemplazo por nueva tecnología

#### Algoritmo
- **Gradient Boosting Regressor** (scikit-learn)
- Entrenado con patrón de crecimiento de 4G (2021-2023)
- Factor de aceleración: **1.3x** (tecnologías recientes se adoptan más rápido)
- Distribución proporcional por departamento

#### Validación
- Comparación con curvas históricas de 3G y LTE
- Análisis de coherencia con tendencias globales
- Validación cruzada del modelo base

### Predicciones 5G

| Año | Centros con 5G | Crecimiento | Penetración |
|-----|----------------|-------------|-------------|
| **2025** | 25,177 | - | ~22% |
| **2026** | 40,645 | +61.4% | ~36% |
| **2027** | 31,825 | -21.7% | ~28% |
| **2028** | 31,825 | 0.0% | ~28% |

#### Top 5 Departamentos (Proyección 2028)

1. **Cundinamarca**: 4,090 centros (12.9%)
2. **Antioquia**: 3,623 centros (11.4%)
3. **Boyacá**: 2,238 centros (7.0%)
4. **Córdoba**: 1,982 centros (6.2%)
5. **Valle del Cauca**: 1,469 centros (4.6%)

### Visualizaciones del Modelo

1. **prediccion_5g_nacional.html** - Proyección nacional con histórico
2. **prediccion_5g_departamentos.html** - Top 8 departamentos
3. **evolucion_tecnologias_historica.html** - Todas las tecnologías (2015-2023)
4. **curva_adopcion_4g.html** - Modelo base para 5G
5. **comparacion_velocidad_adopcion.html** - Comparación 3G vs 4G vs 5G

---

## 📈 Visualizaciones

### Gráficos Generados (Total: 16 archivos HTML)

#### Análisis Histórico
- `crecimiento_cobertura_movil_por_tecnologia.html`
- `evolucion_cuota_mercado_interactiva.html`
- `cuota_mercado_todas_tecnologias.html`
- `lideres_mercado_por_tecnologia.html`
- `velocidad_adopcion_interactiva.html`

#### Mapas Geográficos
- `mapa_cobertura_4g_municipios.html`
- `mapa_proveedores_4g.html`
- `mapa_tecnologias.html`
- `mapa_brechas_4g.html`
- `mapa_lte_penetracion.html`
- `mapa_centros_departamento.html`

#### Predicciones ML
- `prediccion_5g_nacional.html`
- `prediccion_5g_departamentos.html`
- `evolucion_tecnologias_historica.html`
- `curva_adopcion_4g.html`
- `comparacion_velocidad_adopcion.html`

**Todos los gráficos son interactivos** y se pueden abrir directamente en el navegador.

---

## 🚀 Instalación y Uso

### Requisitos Previos
- Python 3.12+
- pip
- Jupyter Notebook o JupyterLab

### Instalación

```bash
# Clonar el repositorio
git clone <repository-url>
cd findal-ds

# Crear entorno virtual
python -m venv venv

# Activar entorno virtual
# En macOS/Linux:
source venv/bin/activate
# En Windows:
venv\Scripts\activate

# Instalar dependencias
pip install -r requirements.txt
```

### Dependencias Principales

```txt
pandas>=2.0.0
numpy>=1.22.0
plotly>=6.0.0
scikit-learn>=1.7.0
jupyter>=1.0.0
nbformat>=5.0.0
nbconvert>=7.0.0
scipy>=1.8.0
```

### Ejecución

#### 1. Análisis Exploratorio

```bash
jupyter notebook exploracion_de_datos.ipynb
```

Este notebook incluye:
- Carga y limpieza de datos
- Análisis estadístico descriptivo
- Generación de gráficos interactivos
- Creación de mapas geográficos

**Tiempo de ejecución estimado**: 3-5 minutos

#### 2. Modelo de Predicción

```bash
jupyter notebook prediccion_expansion_cobertura.ipynb
```

Este notebook incluye:
- Análisis de patrones históricos
- Entrenamiento del modelo
- Generación de predicciones 2025-2028
- Visualizaciones de proyecciones

**Tiempo de ejecución estimado**: 2-3 minutos

### Ejecución por Código

```python
# Ejecutar notebooks programáticamente
import nbformat
from nbconvert.preprocessors import ExecutePreprocessor

# Ejecutar análisis exploratorio
with open('exploracion_de_datos.ipynb') as f:
    nb = nbformat.read(f, as_version=4)
    ep = ExecutePreprocessor(timeout=600, kernel_name='python3')
    ep.preprocess(nb, {'metadata': {'path': '.'}})
```

---

## 💡 Resultados Principales

### Insights Clave

#### 1. Evolución Tecnológica
- **2G** alcanzó su pico en 2021 (35,221 centros)
- **3G** alcanzó su pico en 2022 (37,522 centros)
- **4G** muestra crecimiento desde 2021 (31,266 centros en 2022)
- **LTE** tuvo su pico en 2020 (14,657 centros) antes de consolidarse en 4G

#### 2. Aceleración de Adopción
Cada tecnología se adopta más rápido que la anterior:

| Tecnología | Año 1 | Año 2 | Año 3 |
|------------|-------|-------|-------|
| 3G | 5,190 | 21,236 | 18,504 |
| 4G | 19,367 | 31,266 | 24,481 |
| 5G (pred) | 25,177 | 40,645 | 31,825 |

#### 3. Concentración Geográfica
**Top 5 departamentos por cobertura total:**
1. Cundinamarca: 3,330 centros
2. Antioquia: 3,050 centros
3. Córdoba: 2,730 centros
4. Santander: 2,003 centros
5. Boyacá: 1,941 centros

**Menor cobertura:**
- Vaupés: 54 centros
- Guainía: 69 centros
- San Andrés: 93 centros

#### 4. Proyecciones 5G

**Hallazgos del modelo:**
- Inicio masivo en 2025 con 25,177 centros
- Pico en 2026 con 40,645 centros (+61%)
- Consolidación en 2027-2028 (~31,825 centros)
- Penetración final: ~28% de centros poblados

**Implicaciones estratégicas:**
- 2025-2026: Ventana crítica para inversión
- Cundinamarca y Antioquia: Prioridad geográfica
- Oportunidad para cerrar brechas digitales en regiones periféricas

---

## 📚 Documentación Adicional

### Archivos de Documentación

- **[MODELO_ML.md](MODELO_ML.md)** - Documentación completa del modelo de Machine Learning
  - Metodología detallada
  - Resultados y métricas
  - Limitaciones y supuestos
  - Casos de uso
  - Próximos pasos

### Estructura de Código

Los notebooks están organizados con las siguientes secciones:

#### `exploracion_de_datos.ipynb`
1. Importación de librerías
2. Funciones auxiliares
3. Carga de datos
4. Análisis temporal
5. Análisis de mercado
6. Visualizaciones geográficas

#### `prediccion_expansion_cobertura.ipynb`
1. Carga y preparación de datos
2. Análisis de patrones históricos
3. Modelado de curvas de adopción
4. Generación de predicciones
5. Proyecciones por departamento
6. Comparaciones entre tecnologías
7. Resumen y conclusiones

---

## 🔗 Enlaces Útiles

- **Datos originales**: [Portal de datos abiertos Colombia](https://www.datos.gov.co)
- **DIVIPOLA**: Código de división político-administrativa
- **Plotly**: [Documentación de visualizaciones](https://plotly.com/python/)
- **scikit-learn**: [Documentación de ML](https://scikit-learn.org/)

---

## 👨‍💻 Autor

Proyecto de análisis de datos de cobertura móvil en Colombia

---

## 📄 Licencia

Este proyecto es de código abierto y está disponible para uso educativo y de investigación.

---

## 🙏 Agradecimientos

- Datos proporcionados por proveedores de telecomunicaciones en Colombia
- DIVIPOLA por datos geográficos de centros poblados
- Comunidad de código abierto (Pandas, Plotly, scikit-learn)

---

**Última actualización**: Noviembre 2024
