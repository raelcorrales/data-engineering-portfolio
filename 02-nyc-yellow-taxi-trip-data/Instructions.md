# NYC Yellow Taxi Trip Data

## Descripción del Proyecto

**Objetivo:**
Desarrollar un pipeline ETL (Extracción, Transformación y Carga) para analizar los viajes en taxi amarillo de Nueva York en los meses de enero de 2015 y enero-marzo de 2016. El proyecto incluirá la descarga del dataset, la limpieza de los datos, el análisis y la visualización de métricas clave, y su almacenamiento en un formato accesible para futuras consultas.

**Dataset:**  
[NYC Yellow Taxi Trip Data](https://www.kaggle.com/datasets/elemento/nyc-yellow-taxi-trip-data)
Este conjunto de datos incluye información sobre los viajes en taxi amarillo en Nueva York, como fechas de inicio y finalización del viaje, distancias recorridas, tarifas, tipos de pago, entre otros. La información está agrupada en las siguientes columnas clave:
- **tpep_pickup_datetime**: Fecha y hora de inicio del viaje.
- **tpep_dropoff_datetime**: Fecha y hora de fin del viaje.
- **Passenger_count**: Número de pasajeros.
- **Trip_distance**: Distancia del viaje en millas.
- **Pickup_latitude / Pickup_longitude**: Coordenadas de recogida.
- **Dropoff_latitude / Dropoff_longitude**: Coordenadas de entrega.
- **Fare_amount**: Monto de la tarifa del viaje.
- **Tip_amount**: Monto de la propina.
- **Total_amount**: Monto total cobrado.

---

## Requisitos

### Dependencias
- **opendatasets**: Para descargar el dataset de Kaggle.
- **pandas**: Para manipular y transformar los datos.
- **sqlite3**: Para almacenar los datos en una base de datos SQLite.
- **seaborn**: Para la visualización de datos.
- **matplotlib**: Para crear gráficos.
- **schedule**: Para automatizar la ejecución del pipeline.

### Variables de Entorno
- **KAGGLE_USERNAME**: Usuario de Kaggle necesario para descargar el dataset.
- **KAGGLE_KEY**: Key de Kaggle necesario para descargar el dataset.

### Funcionalidad

1. **Extracción de Datos**:
   - Descargar el dataset desde Kaggle utilizando `opendatasets`.
   - Leer el archivo CSV con `pandas` y crear un DataFrame.

2. **Transformación de Datos**:

   - **Limpieza de Datos**:
     - Eliminar filas con valores faltantes en columnas clave (por ejemplo, `tpep_pickup_datetime`, `tpep_dropoff_datetime`, `Trip_distance`, etc.).
     - Corregir errores en los formatos de fecha y hora (en caso de que existan).
     - Eliminar columnas irrelevantes (por ejemplo, `VendorID`, que no tiene mucha utilidad para el análisis inicial).

   - **Enriquecimiento de Datos**:
     - Calcular una nueva columna **"Duración del Viaje"** a partir de la diferencia entre `tpep_dropoff_datetime` y `tpep_pickup_datetime`.
     - Convertir las coordenadas de recogida y entrega a una representación más útil para el análisis, si es necesario.
     - Calcular métricas como el **"Ingreso por Kilómetro"** (`Fare_amount / Trip_distance`) y **"Propina Promedio"** por tipo de pago.
   
   - **Agregación de Datos**:
     - Agrupar los datos por **mes** y **zona geográfica** (si se dispone de las coordenadas).
     - Calcular estadísticas como el **"Promedio de Ingreso"**, **"Promedio de Propinas"**, **"Promedio de Distancia"** y **"Promedio de Tarifa"** para cada grupo.

3. **Carga de Datos**:
   - Guardar los datos transformados en un archivo CSV llamado `taxi_trip_data_transformado.csv`.
   - Almacenar los datos en una base de datos SQLite para realizar consultas más complejas si es necesario.

4. **Automatización**:
   - Crear un script para ejecutar el pipeline ETL de manera automática cada 24 horas.
   - Usar la librería `schedule` para automatizar la ejecución del pipeline.
   
   **Opciones de Automatización**:
   - Usar cron en Linux, Task Scheduler en Windows, o Github Actions para ejecutar el script automáticamente.

---

## Criterios de Aceptación

1. **Extracción de Datos**:
   - El script debe descargar correctamente el dataset desde Kaggle y cargarlo en un DataFrame.
   
2. **Transformación de Datos**:
   - El proceso de limpieza debe eliminar filas con datos faltantes en columnas clave.
   - La columna **"Duración del Viaje"** debe calcularse correctamente.
   - Las métricas como **"Ingreso por Kilómetro"** y **"Propina Promedio"** deben ser correctas.
   - Los datos deben estar correctamente agregados por mes y zona (si es posible).

3. **Carga de Datos**:
   - Los datos transformados deben guardarse correctamente en un archivo CSV y deben poder ser cargados en una base de datos SQLite.

4. **Automatización**:
   - El pipeline debe ejecutarse automáticamente cada 24 horas utilizando una de las opciones de automatización mencionadas (cron, schedule, Github Actions).

5. **Generales**:
   - El código debe ser modular, bien estructurado y documentado.
   - El README debe contener instrucciones claras sobre cómo instalar dependencias, ejecutar el pipeline y configurar la automatización.
   - El proyecto debe seguir las mejores prácticas de desarrollo, con un manejo adecuado de errores y validación de los datos.
