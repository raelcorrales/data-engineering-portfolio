# Analisis de Ventas de Video Juegos.

### Requerimientos
- opendatasets
- sqlite3
- pandas
- seaborn
- matplotlib

### Variables de Entorno
- **KAGGLE_USERNAME**: Usuario de Kaggle necesario para descargar el dataset.
- **KAGGLE_KEY**: Key de Kaggle necesario para descargar el dataset.

### Extracción de Datos
- El script debe descargar el dataset "Video Game Sales" de Kaggle en formato CSV si no existe localmente.
- Se debe utilizar la librería `pandas` para leer el archivo CSV y crear un DataFrame.
- El script debe manejar excepciones en caso de que el archivo CSV no exista o no se pueda leer.

### Transformación de Datos

#### Limpieza:
- Se deben eliminar filas con valores faltantes en columnas críticas para el análisis (ej. Nombre del Juego, Año de Lanzamiento).
- Se deben corregir errores de formato en columnas como "Año de Lanzamiento" (ej. convertir a formato de fecha).
- Se deben eliminar columnas irrelevantes para el análisis (ej. ID del juego).

#### Enriquecimiento:
- Se debe crear una nueva columna "Década de Lanzamiento" basada en la columna "Año de Lanzamiento".
- Se deben calcular métricas relevantes como "Ventas Totales" (suma de ventas globales).

#### Agregación:
- Se deben agrupar los datos por categorías como "Género", "Plataforma" y "Década de Lanzamiento".
- Se deben calcular estadísticas como "Ventas Promedio" y "Cantidad de Juegos" para cada grupo.

### Carga de Datos
- Los datos transformados se deben guardar en un nuevo archivo CSV llamado `vgsales_transformado.csv`.
- El script debe permitir la opción de cargar los datos en una base de datos SQLite en lugar de un archivo CSV.

### Automatización (Challenge)

- Se debe crear un script que ejecute el pipeline ETL automáticamente cada 24 horas (o el intervalo de tiempo que se defina).
- Se debe utilizar la librería `schedule` para la automatización.

### Generales
- El código debe ser legible y estar bien documentado.
- El proyecto debe seguir las mejores prácticas de desarrollo de software.
- El README debe estar completo y actualizado, incluyendo instrucciones claras sobre cómo ejecutar el pipeline ETL.

### Criterios de Aceptación Adicionales (Opcionales)
- Se puede agregar un sistema de registro (logging) para monitorear el pipeline y detectar posibles errores.
- Se puede explorar el uso de un framework de ETL como Apache Airflow para proyectos más complejos.

