# 📊 Pipeline ETL de Ventas Diarias con Python

## 📌 Descripción del proyecto

Este proyecto consiste en el desarrollo de un **pipeline ETL (Extract, Transform, Load)** en Python, diseñado para automatizar el procesamiento de las ventas diarias de una tienda online.

El sistema recibe un archivo CSV con las transacciones del día anterior, limpia y valida los datos, calcula indicadores comerciales y genera un reporte en formato JSON con información relevante para la toma de decisiones.

El principal desafío es garantizar que el proceso sea robusto y pueda continuar funcionando ante registros incompletos, formatos incorrectos o datos inconsistentes, sin perder de vista la calidad de la información.

## 🎯 Objetivos del proyecto

* Automatizar el procesamiento de transacciones comerciales.
* Implementar reglas de limpieza y validación de datos.
* Transformar información inconsistente en datos útiles para el análisis.
* Calcular métricas de ventas y agrupar resultados por categoría.
* Generar reportes estructurados para su posterior consumo por otros sistemas o herramientas de análisis.
* Registrar errores y permitir que el proceso continúe cuando una transacción presenta problemas.

## 🏢 Problema de negocio

Una tienda online genera diariamente un archivo CSV con las ventas realizadas. Sin embargo, los datos pueden contener valores faltantes, precios con formatos incorrectos y fechas inconsistentes.

Procesar estos archivos manualmente consume tiempo y aumenta el riesgo de errores, lo que puede afectar la confiabilidad de los indicadores utilizados por la gerencia.

**La solución propuesta** es desarrollar un proceso automatizado que transforme los datos originales en un reporte confiable, facilitando el seguimiento del rendimiento comercial y reduciendo las tareas manuales.

### 📥 Entrada

Archivo CSV con las siguientes columnas:

* `fecha`: fecha de la transacción.
* `producto`: producto vendido.
* `categoria`: categoría comercial.
* `cantidad`: unidades vendidas.
* `precio_unitario`: precio por unidad.
* `cliente`: identificador o nombre del cliente.

### ⚙️ Procesamiento

* Lectura del archivo de origen.
* Validación de campos obligatorios y formatos.
* Detección y tratamiento de registros inconsistentes.
* Conversión de tipos de datos.
* Cálculo de importes por transacción.
* Agrupación de resultados por categoría.
* Registro de errores para facilitar su análisis.

### 📤 Salida

El pipeline genera archivos JSON con los resultados del procesamiento:

* `resumen_dia.json`: resumen de ventas e indicadores comerciales.
* `errores_dia.json`: registros o incidencias detectadas durante la ejecución.

## 🔄 Arquitectura del pipeline ETL

El proceso se organiza en tres etapas principales:

**1. Extract — Extracción**

Se lee el archivo CSV que contiene las transacciones diarias y se prepara la información para su procesamiento.

**2. Transform — Transformación**

Se aplican reglas de validación y limpieza, se normalizan los formatos y se calculan las métricas necesarias. Los registros problemáticos se identifican y se registran sin interrumpir el procesamiento de las demás transacciones.

**3. Load — Carga**

Se generan los archivos JSON con el resumen ejecutivo y los errores detectados, dejando la información estructurada para su consulta y análisis posterior.

## 🗂️ Estructura del proyecto

```text
pipeline-ventas-csv/
│
├── data/
│   ├── ventas_diarias.csv
│   ├── resumen_dia.json
│   └── errores_dia.json
│
├── generar_datos.py
├── pipeline_ventas.py
├── Main.py
├── .gitignore
└── README.md
```

### 📁 Descripción de los archivos

| Archivo              | Responsabilidad                                                                            |
| -------------------- | ------------------------------------------------------------------------------------------ |
| `generar_datos.py`   | Genera un conjunto de datos de prueba para simular las ventas diarias.                     |
| `pipeline_ventas.py` | Contiene la lógica de extracción, transformación, validación y procesamiento de los datos. |
| `Main.py`            | Coordina la ejecución del pipeline.                                                        |
| `ventas_diarias.csv` | Archivo de entrada con las transacciones comerciales.                                      |
| `resumen_dia.json`   | Archivo de salida con el resumen de ventas.                                                |
| `errores_dia.json`   | Archivo de salida con los errores e inconsistencias detectados.                            |
| `.gitignore`         | Define los archivos y directorios que Git debe excluir del seguimiento.                    |

## 🛠️ Tecnologías utilizadas

* **Python:** desarrollo de la lógica de procesamiento y automatización.
* **CSV:** formato de entrada para la información transaccional.
* **JSON:** formato de salida para almacenar resultados estructurados.
* **Git y GitHub:** control de versiones y documentación del proyecto.

## 🚀 Instalación y ejecución

### 1. Clonar el repositorio

```bash
git clone https://github.com/lucascarrizo10/pipeline-ventas-csv.git
cd pipeline-ventas-csv
```

### 2. Verificar la instalación de Python

Se requiere una versión de Python 3 compatible con el código del proyecto.

```bash
python --version
```

### 3. Generar los datos de prueba

Desde la raíz del proyecto, ejecutar:

```bash
python generar_datos.py
```

Este script prepara un conjunto de datos para probar el funcionamiento del pipeline.

### 4. Ejecutar el pipeline

```bash
python Main.py
```

Al finalizar, se espera que el proceso genere el resumen diario y el archivo de errores correspondientes, según las reglas implementadas.

## 📈 Indicadores de negocio

El reporte está orientado a facilitar el seguimiento de las ventas y responder preguntas como:

* ¿Cuál fue el importe total vendido durante el día?
* ¿Qué categorías generaron mayor volumen de ventas?
* ¿Cuántas transacciones pudieron procesarse correctamente?
* ¿Qué registros presentan inconsistencias?
* ¿Qué problemas de calidad de datos necesitan revisión?

Estos indicadores permiten transformar registros transaccionales en información útil para el seguimiento del negocio. Las métricas definitivas dependerán de las reglas implementadas en el código.

## 🧪 Calidad y confiabilidad de los datos

Uno de los principales objetivos es evitar que un único registro defectuoso interrumpa todo el proceso.

Para ello, el diseño contempla:

* Validación de campos y tipos de datos.
* Detección de valores faltantes.
* Identificación de precios y fechas con formatos incorrectos.
* Registro de errores para facilitar su seguimiento.
* Separación entre los datos procesables y las incidencias detectadas.

El objetivo no es solamente generar un reporte, sino también **hacer visible la calidad de los datos utilizados para construirlo**.

## 💡 Aprendizajes y valor del proyecto

Este proyecto permite aplicar conceptos fundamentales de ingeniería y análisis de datos en un escenario de negocio realista.

Entre los principales aprendizajes se encuentran:

* Diseño de procesos ETL.
* Automatización del procesamiento de archivos.
* Validación y transformación de datos.
* Generación de reportes estructurados.
* Manejo de errores y tolerancia a fallos.
* Organización y documentación de código Python.
* Comprensión de la relación entre calidad de datos e indicadores de negocio.

## 🔮 Posibles mejoras futuras

Como evolución del proyecto, se podrían incorporar:

* **Pandas:** para facilitar el procesamiento de grandes volúmenes de datos.
* **SQL Server:** para almacenar las transacciones procesadas y construir un historial de ventas.
* **Power BI:** para desarrollar un dashboard de seguimiento comercial.
* **Logging:** para mantener un registro detallado de las ejecuciones y sus incidencias.
* **Automatización programada:** para ejecutar el pipeline diariamente sin intervención manual.
* **Pruebas automatizadas:** para verificar las reglas de validación y los resultados calculados.
* **Alertas de calidad:** para notificar cuando se detecten errores o anomalías relevantes.

## 👨‍💻 Autor

Proyecto personal desarrollado como parte de mi formación en análisis e ingeniería de datos, con foco en la automatización de procesos ETL, la calidad de la información y la generación de valor para el negocio.
