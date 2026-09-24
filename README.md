# Laboratorio 7 — Spark MLlib (CC3066 Data Science, UVG)

Análisis de salarios de asalariados con la ENEIC (INE Guatemala) usando Python y Spark 3.5 (`pyspark.ml`).

## Requisitos

- Docker y Docker Compose.
- Archivos Excel de la base de **Personas** de la ENEIC (I–IV 2025 y I 2026) y sus diccionarios.

## 1. Colocar los datos

Crear la carpeta `working_dir/raw/` y copiar los cinco Excel con estos nombres (si se usan otros, cambiar la tabla `ARCHIVOS` en la sección 0 del notebook):

```
working_dir/raw/
├── personas_2025T1.xlsx
├── personas_2025T2.xlsx
├── personas_2025T3.xlsx
├── personas_2025T4.xlsx
├── personas_2026T1.xlsx
└── diccionarios/
```

Los datos, Parquet y modelos **no** se suben a Git (ver `.gitignore`).

## 2. Levantar el entorno

```bash
docker compose build        # la primera vez, o después de cambiar el dockerfile
docker compose up
```

Abrir `http://localhost:8888`. El contenedor trae Python 3.11, OpenJDK 17, PySpark 3.5.1, pandas, openpyxl, matplotlib y seaborn.

Si en Linux aparece un error de permisos al escribir en `working_dir/`, ejecutar en el host:

```bash
chmod -R a+rwX working_dir notebooks
```

## 3. Ejecutar

- Notebook final: `notebooks/lab7_spark_mllib.ipynb` → *Kernel ▸ Restart & Run All*.
- Borradores por integrante: `notebooks/dev/`.

Todas las rutas se definen en la celda de configuración (`BASE_DIR = /opt/app/working_dir`). Fuera de Docker se puede usar otra ruta con la variable de entorno `LAB7_BASE`.

## Estructura

```
├── dockerfile
├── docker-compose.yml
├── README.md
├── TAREAS.md
├── notebooks/
│   ├── lab7_spark_mllib.ipynb
│   └── dev/
└── working_dir/
    ├── raw/            # Excel originales (no versionado)
    ├── parquet/        # staging/, prep_2025/, prep_2026/
    ├── models/         # lr_best/, rf_best/, lr_final/, rf_final/
    └── figures/
```