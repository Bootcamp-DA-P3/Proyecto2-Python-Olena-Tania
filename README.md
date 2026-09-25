# Proyecto2-Python-Olena-Tania
Procesamiento y limpieza de datos con Python a dataset KIVA

Este repositorio contiene el flujo de trabajo completo para la **exploración, diagnóstico, limpieza, transformación y validación de calidad** del conjunto de datos de préstamos de **Kiva** (`kiva_loans.csv`).

El objetivo principal es transformar un conjunto de datos en bruto (*raw*) en un *dataset* analítico pulido, estandarizado y listo para futuro análisis.

Resumen de la Metodología de Limpieza
El notebook está estructurado siguiendo una metodología rigurosa de 6 pasos:
	Importación: Carga de datos.
	
  Análisis Exploratorio Rápido (EDA): Verificación inicial de dimensiones, tipos de variables y resúmenes estadísticos.
	
  Diagnóstico de Problemas y Transformaciones y Limpieza:
	  - Detección de duplicados e inconsistencias de formato.
    - Deduplicación interna: Limpieza de etiquetas repetidas dentro de celdas individuales en la columna tags (ej. #Health, #Health → #Health).
    - Tipos de Datos: Conversión de campos temporales (posted_time, disbursed_time, funded_time, date) a datetime64.
	  - Verificación de variables de texto.
    - Codificación variables categóricas: 
        borrows_genders, una nueva variable con 3 categegorias (female, male y several).
        Continent que agrupa registros de países por continentes.
	  - Tratamiento de Nulos: Reemplazo de nulos categóricos por marcas explícitas ('Unspicified').
	  - Identificación visual de outliers en variables financieras. 
    - Hemos creado nuevas columnas para la aplicación de transformación logaritmica de variables log_funded_amount, log_loan_amount,log_lender_count.
	  - Crear columnas derivadas útiles (ej.: año, mes, ratio)
	      funded_ratio: Proporción del dinero financiado vs. solicitado ("funded_amount"/"loan_amount" ).
	      amount_per_lender: Aporte promedio por prestamista con manejo seguro de división entre cero.
    
	Validación Post-Limpieza (Data Quality Checks):
	  - Pruebas automáticas de unicidad de ID clave (id).
	  - Verificación de cero nulos en variables primarias.
	  - Conteos esperados: Validación de total de filas.
    - Snapshot de Archivo original (raw) y Archivo final limpiio, para comprobar dimensiones generales y sus cambios.
  
  Exportación: Guardado del archivo estructurado final kiva_limpio.csv.

