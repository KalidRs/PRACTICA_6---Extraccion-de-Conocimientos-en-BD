# PRACTICA_6

Este proyecto contiene una práctica de análisis y procesamiento de datos usando Python (Jupyter Notebook), con énfasis en la manipulación de archivos CSV y la integración con bases de datos MySQL.

## Estructura del Proyecto

```
PRACTICA_6/
├── .gitignore
├── comentarios_filtrados.csv
├── Practica_6.ipynb
├── salaries.csv
└── users_placeholder.csv
```

## Descripción de la Práctica

### 1. Lectura de Datos

- Se utiliza la librería `pandas` para leer el archivo `salaries.csv` y cargarlo en un DataFrame:
    ```python
    df = pd.read_csv('salaries.csv')
    ```

### 2. Exploración y Limpieza de Datos

- Se explora la estructura y los metadatos del DataFrame para entender el contenido y la calidad de los datos.
- Se realiza limpieza y transformación de los datos, incluyendo la selección y renombrado de columnas relevantes.

### 3. Exportación de Datos

- **Exportar a CSV:**  
  El DataFrame limpio (`df_clean`) se exporta a un archivo CSV llamado `users_placeholder.csv` sin incluir el índice:
    ```python
    df_clean.to_csv("users_placeholder.csv", index=False)
    print(" users_placeholder.csv generado")
    ```
- **Exportar a MySQL:**  
  Se utiliza SQLAlchemy para guardar el DataFrame como una tabla llamada `users_api` en una base de datos MySQL:
    ```python
    from sqlalchemy import create_engine
    df_clean.to_sql(
        name='users_api',
        con=engine,
        if_exists='replace',
        index=False
    )
    print(" Tabla 'users_api' creada en MySQL")
    ```


## Ejecución y Resultados

- Al ejecutar las celdas del notebook `Practica_6.ipynb`, se generan los siguientes mensajes de log:
    ```
     users_placeholder.csv generado
     Tabla 'users_api' creada en MySQL
    ```

## Requisitos

- Python 3.x
- Jupyter Notebook
- pandas
- sqlalchemy
- MySQL (para la exportación a base de datos)

## Notas

- Los archivos CSV generados y utilizados están ignorados por git para evitar conflictos y mantener el repositorio limpio.
- El notebook contiene todo el flujo de trabajo, desde la carga de datos hasta la exportación a