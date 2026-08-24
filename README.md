# Prueba práctica — Analista de datos

El proyecto se divide en tres partes que contienen el desarrollo de los ejercicios de la prueba práctica:

1. **Segmentación de comercios mediante RFM:** análisis de los comercios y las transacciones realizadas por la API, con el fin de caracterizar segmentos de comercios según su comportamiento de recencia, frecuencia y valor monetario. El proceso genera el archivo data_segmentacion.csv con los resultados, y se complementa con un dashboard en Power BI para el monitoreo de la estrategia de segmentación, para conseguir el aumento esperado de las comisiones por el uso de la API. Los archivos con el desarrollo de esta parte son:

    - [`01_segmentacion_clientes.ipynb`](notebooks/01_segmentacion_clientes.ipynb)
    - [`dashboard/dashboard.pbix`](dashboard/dashboard.pbix)

2. **Análisis de series de tiempo:** para la Tasa Representativa del Mercado (TCRM), incluyendo un análisis descriptivo y exploratio, identificación de los componentes de la serie, y evaluación y validación de pronósticos.Los archivos con el desarrollo de esta parte son:
 
    - [`notebooks/02_series_tiempo_tcrm.ipynb`](notebooks/02_series_tiempo_tcrm.ipynb)

3. **Preguntas y problemas de marketing:** Solución a preguntas relacionadas con marketing y estrategias de campañas, analizando los resultados y brindando recomendaciones.
    - [`notebooks/03_marketing_estrategias.ipynb`](notebooks/03_marketing_estrategias.ipynb)

## Estructura del proyecto

```
Prueba/
├── README.md                  
├── requirements.txt           # Dependencias de Python (versiones fijadas)
├── notebooks/                 # Desarrollo de los ejercicios
│   ├── 01_segmentacion_clientes.ipynb
│   ├── 02_series_tiempo_tcrm.ipynb
│   └── 03_marketing_estrategias.ipynb
├── data/
│   ├── raw/                   # Datos de entrada
│   │  ├── DataTransacciones_PruebasIngreso.xlsx
│   │  └── Tasa_de_Cambio_Representativa_del__Mercado_Historico.xlsx
│   └── processed/             # Salidas generadas
│       └── data_segmentacion.csv
├── dashboard/                 # Visualización en Power BI
│   ├── dashboard.pbix
│   └── assets/                # elementos utilizados (no relevante)
│       └── fondo3.jpg         
└── docs/                      # Documentación
    ├── prueba-practica-analista-datos.pdf   # Enunciado de la prueba
    └── slides.pdf                           # Presentación de resultados
```

## Requisitos

- **Python 3.14**
- Para visualizar el dashboard: **Power BI Versión: 2.157.879.0 64-bit (August 2026)** (solo Windows).

> Los notebooks fueron desarrollados y probados con Python 3.14 sobre Windows.

## Instalación

1. Clonar o descargar el proyecto y ubicarse en la carpeta raíz.

2. Crear el entorno virtual:

   ```powershell
   python -m venv .venv
   ```

3. Activar el entorno virtual:

   - **PowerShell:**

     ```powershell
     .\.venv\Scripts\Activate.ps1
     ```

   - **CMD:**

     ```cmd
     .venv\Scripts\activate.bat
     ```

   - **Git Bash:**

     ```bash
     source .venv/Scripts/activate
     ```

4. Instalar las dependencias:

   ```powershell
   pip install -r requirements.txt
   ```

## Ejecución (opcional)

Los notebooks pueden revisarse directamente (incluyen salidas ya ejecutadas), pero si se desea re-ejecutarlos:

### Opción A — VS Code (recomendada)

1. Abrir la carpeta del proyecto en VS Code.
2. Instalar las extensiones **Python** y **Jupyter**.
3. Seleccionar como kernel el intérprete del entorno virtual: `.venv\Scripts\python.exe`.
   > El paquete `ipykernel` es necesario; instalarlo con `pip install ipykernel` si no está disponible.
4. Abrir cada notebook dentro de `notebooks/` y ejecutar todas las celdas (`Run All`), respetando el orden indicado abajo.

### Opción B — Jupyter desde el navegador

```powershell
pip install jupyterlab
jupyter lab notebooks
```

Luego abrir los notebooks desde la interfaz web.

## Guía de revisión

### Parte 1 — Segmentación de clientes ([`01_segmentacion_clientes.ipynb`](notebooks/01_segmentacion_clientes.ipynb), [`dashboard.pbix`](dashboard\dashboard.pbix))

- Lectura y limpieza de [`data/raw/DataTransacciones_PruebasIngreso.xlsx`](\data\raw\DataTransacciones_PruebasIngreso.xlsx) (comercios y transacciones).
- Elección y construcción de variables **RFM** (Recencia, Frecuencia, Monto) para la segmentación de los comercios.
- Asignación de segmentos, análsis de resultados y exportación de archivo con la segmentación [`data/processed/data_segmentacion.csv`](data/processed/data_segmentacion.csv).
- Propuesta de seguimiento a la metodología en [`01_segmentacion_clientes.ipynb`](notebooks/01_segmentacion_clientes.ipynb) y desarrollo del dashboard según el diseño propuesto [`dashboard/dashboard.pbix`](dashboard/dashboard.pbix).

  > Si se desean actualizar los datos, verificar fuentes en Power Query del `.pbix`.

- [`data_segmentacion.csv`](data/processed/data_segmentacion.csv) contiene una fila por cliente con sus métricas RFM y su segmento, y se usa para el desarrollo del dashboard.

### Parte 2 — Series de tiempo TCRM ([`notebooks/02_series_tiempo_tcrm.ipynb`](notebooks/02_series_tiempo_tcrm.ipynb))

- Carga y exploración del histórico [`data/raw/Tasa_de_Cambio_Representativa_del__Mercado_Historico.xlsx`](data/raw/Tasa_de_Cambio_Representativa_del__Mercado_Historico.xlsx).
- Análisis exploratorio, descomposición de la serie y verificación de estacionariedad (prueba **ADF**), autocorrelaciones (**ACF/PACF**).
- Identificaciónd e modelos óptimos a partir del EDA y función **auto-arima** (`pmdarima`) y evaluación con métricas como **MAPE** (`sklearn.metrics`).
- Validación del pronóstico y recomendaciones.

### Parte 3 — Marketing y estrategias de campaña ([`notebooks/03_marketing_estrategias.ipynb`](notebooks/03_marketing_estrategias.ipynb))

- Desarrollo de las preguntas y problemas planteados sobre marketing y estrategias de campaña.

### Material de apoyo

- `docs/prueba-practica-analista-datos.pdf`: enunciado completo de la prueba.
- `docs/slides.pdf`: presentación con los resultados y conclusiones del proyecto.

### Referencias

- [RFM: definición, propósito y ejemplos](https://mailchimp.com/es/resources/rfm-analysis/)
- [GTM](https://marketingplatform.google.com/intl/es/about/tag-manager/features/#integrations)
- [Guía completa sobre alcance y publicidad](https://spideraf.com/es/articles/guia-completa-sobre-frecuencia-y-alcance-en-publicidad)
