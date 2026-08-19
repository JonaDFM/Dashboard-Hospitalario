# Análisis de Eficiencia Hospitalaria - Power BI

Dashboard interactivo desarrollado en Microsoft Power BI para analizar el rendimiento y la eficiencia de diversas instalaciones hospitalarias. 

* **Volumen de Datos:** Procesamiento y modelado de **2,346,931 registros** de altas de pacientes.
* **Objetivo:** Evaluar indicadores clave de rendimiento (KPIs) como el costo promedio, la duración de la estancia (LOS) y el porcentaje de altas a domicilio.
* **Tecnologías:** Power BI Desktop, Power Query (Transformación y limpieza de datos), DAX (Modelado y cálculos dinámicos).

## Vistas del Dashboard
<img width="908" height="508" alt="image" src="https://github.com/user-attachments/assets/fbca664e-4671-4dda-a916-77a23d873ec6" />
<img width="916" height="505" alt="image" src="https://github.com/user-attachments/assets/4a6c53fa-1efb-44d1-9a26-8fe86a1d707c" />
<img width="902" height="503" alt="image" src="https://github.com/user-attachments/assets/2adbcef6-9997-46d2-9541-f80d5b518981" />


## Código DAX
El proyecto incluye cálculos avanzados para medir la eficiencia hospitalaria comparando el rendimiento individual contra la media general.

```Total_Altas = COUNTROWS('Altas_Pacientes_Hospitalizados')```

Esta fórmula obtiene el número total de filas o registros de la tabla “AltasPacientes_Hospitalizados” y lo almacena en “Total_Altas”.

```Promedio_LOS = AVERAGE('Altas_Pacientes_Hospitalizados'[Duración de la Estancia])```

Esta fórmula obtiene el promedio general de los días de estancia de los pacientes en el hospital y lo almacena en “Promedio_LOS”.

```Costo_Promedio = AVERAGE('Altas_Pacientes_Hospitalizados'[Costos Totales])```

Esta fórmula obtiene el promedio general de los costos totales de un paciente hospitalizado, para saber cuánto es el promedio que cuesta la hospitalización de alguien.

```Costo_Total = SUM(Altas_Pacientes_Hospitalizados[Costos Totales])```

Esta fórmula obtiene la suma de todos los costos totales de los pacientes hospitalizados, permite saber los gastos acumulados de los pacientes dados de alta.

```LOS_vs_Promedio = [Promedio_LOS] - CALCULATE([Promedio_LOS], ALL(Altas_Pacientes_Hospitalizados[Nombre de la Instalación]))```

Esta fórmula compara el promedio de estancia del contexto actual (si hay un filtro aplicado) contra el promedio general. Usa ALL() para ignorar los filtros aplicados al "Nombre de la Instalación" y obtener la media general. Si el resultado es negativo, significa que los pacientes filtrados salen más rápido que el promedio general.
