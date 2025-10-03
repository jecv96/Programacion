# Flujo de Trabajo para Procesamiento de Datos MODFLOW

Este proyecto proporciona un flujo de trabajo completo para el pre-procesamiento y post-procesamiento de datos de niveles observados y simulados obtenidos de modelos de aguas subterráneas MODFLOW.

## Estructura del Proyecto

```
modflow_workflow/
├── data/
│   ├── raw/              # Datos originales (.hds, .obs, .cbb)
│   ├── processed/        # Datos procesados y limpiados
│   └── output/           # Resultados y análisis finales
├── scripts/             # Funciones auxiliares
├── notebooks/          # Jupyter notebooks con ejemplos
├── figures/            # Gráficos y visualizaciones
├── reports/            # Reportes generados
├── requirements.txt    # Dependencias de Python
└── README.md          # Este archivo
```

## Características Principales

### Pre-procesamiento
- ✅ Lectura de archivos MODFLOW (.hds, .obs)
- ✅ Limpieza y validación de datos
- ✅ Detección y manejo de valores faltantes
- ✅ Filtrado de datos fuera de rango

### Post-procesamiento
- ✅ Análisis estadístico comparativo
- ✅ Cálculo de métricas de rendimiento (MAE, RMSE, R², NSE)
- ✅ Análisis por pozo individual
- ✅ Generación de visualizaciones
- ✅ Mapas de contornos de cabezas

### Visualizaciones
- 📈 Series temporales observado vs simulado
- 📊 Gráficos de dispersión
- 📉 Análisis de residuos
- 🗺️ Mapas de contornos de cabezas

## Instalación

1. Clonar o descargar el proyecto
2. Instalar dependencias:
```bash
pip install -r requirements.txt
```

## Uso Rápido

```python
from notebooks.modflow_data_processing import process_modflow_data

# Procesar datos completos
results = process_modflow_data(
    observed_file="data/raw/observations.obs",
    simulated_file="data/raw/simulated.obs", 
    head_file="data/raw/model.hds",
    well_locations=[(10, 15), (20, 25), (30, 35)],
    nrow=50, ncol=60,
    output_dir="results/analysis_2024",
    project_name="mi_proyecto_modflow"
)
```

## Formato de Archivos de Entrada

### Archivo de Observaciones (.obs)
```
# Comentarios opcionales
PZ01 0.0 105.2
PZ01 30.0 104.8
PZ02 0.0 98.5
PZ02 30.0 98.1
```

### Archivo de Cabezas (.hds)
- Archivo binario generado por MODFLOW
- Requiere especificar dimensiones de la grilla (nrow, ncol)

## Métricas de Evaluación

- **MAE**: Error absoluto medio (metros)
- **RMSE**: Error cuadrático medio (metros)
- **R²**: Coeficiente de determinación (0-1)
- **NSE**: Eficiencia Nash-Sutcliffe (-∞ a 1)

### Criterios de Evaluación
- NSE > 0.7: Excelente ajuste
- NSE > 0.5: Ajuste aceptable
- NSE < 0.5: Ajuste deficiente

## Archivos de Salida

- `observed_clean.csv`: Datos observados limpios
- `simulated_clean.csv`: Datos simulados limpios
- `merged_data.csv`: Datos fusionados para análisis
- `well_statistics.csv`: Estadísticas por pozo
- `global_statistics.csv`: Estadísticas globales
- `analysis_report.txt`: Reporte de análisis
- Gráficos PNG: Series temporales, dispersión, residuos, contornos

## Ejemplos

Ver el notebook `notebooks/modflow_data_processing.ipynb` para ejemplos completos con datos sintéticos.

## Contribuciones

Este proyecto está diseñado para ser extensible. Puedes:
- Añadir nuevas métricas de evaluación
- Implementar visualizaciones adicionales
- Integrar con otros formatos de archivos MODFLOW
- Mejorar el manejo de errores

## Licencia

Proyecto educativo para el Diplomado en Hidrogeología UM.
