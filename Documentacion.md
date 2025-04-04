# Documentación de la exploración básica de los datos.

## 1. Carga de datos y análisis básico exploratorio con primeras impresiones.
- Hay dos df que se pueden unir por 'Loyalty number', pero al poner 'index_col=0' convierte esta columna, la primera en el índice de cada df, por eso no sale en info como columna. Si se quiere volver a poner como columna: df_vuelos.reset_index(inplace=True)
- Parece que no hay nulos.

    Posibles pasos:
    - Búsqueda de nulos.
    - Búsqueda de duplicados.
    - Cambiar tipo de datos.
    - Búsqueda de datos negativos.
    - Bucle para ver los datos únicos.
    - Ver describe.
    - Convertir texto a minúscula y eliminar espacios.
    - Corregir erratas si las hay.

    1. En el df_clientes hay nulos en Salary, Cancellation Year y Cancellation Month.
        - En el df_ vuelos no hay nulos.
        - Se puede hacer una __columna nueva de cuales están activos e inactivos por los nulos en cancellation__, creo que puede ser muy interesante para sacar posibles datos en el futuro de su actividad antes de cancelar o por qué han cancelado.
        - Los nulos de Salary también puede ser porque no tengan trabajo o estén estudiando. Se comprueba si los valores únicos de los Nan de Salary corresponden a College y así es.

    2. Hacemos un bucle para buscar los valores únicos y así ver inconsistencias o errores tipográficos.
        - En df_clientes __Country__ solo tiene un valor único, se podría eliminar la columna si la empresa solo tuviera clientes de ese país, pero puede que busque ampliar los países.
        - No hay errores tipográficos en ninguno de los dos.
        - Hay que cambiar varios float a int en los dos df: points accumulated (vuelos) y cancellation month/year (clientes).

    3. Hacemos otro para ver si hay valores negativos, ya que no se ven todos los únicos en algunas columnas.
        - En df_vuelos no hay valores negativos.
        - En df_clientes hay 20 valores negativos en Salary, se pueden cambiar a positivos ya que parece un error al meter los datos y dejamos los Nan.

    4. Buscamos duplicados.
        - En clientes no hay.
        - En vuelos hay 228705: entendemos que cada cliente vuela varias veces, por eso hay varios registros del mismo cliente.

## 2. Limpieza y cambios

1. FLOAT a INT: points accumulated (vuelos) y cancellation month/year (clientes). Este último hay que tener en cuenta que tienen NaN, por lo que habrá que poner Int64 para mantenerlos.

2. Cambiamos los __valores negativos__ de salary a positivos.

3. Buscamos y eliminamos los __duplicados__ pero cuando todas las columnas sean idénticas, porque un mismo cliente puede volar muchas veces. Al principio había 405624 registros, duplicados generales 228705 y se han eliminado __1864__ duplicados exactos porque en el shape final nos salen 403760 filas.

4. Creamos una __nueva columna (Is_Active)__ con respuesta True/False por los nulos de Cancellation: es un dato importante para la empresa saber si está o no en activo. Hay 14670 en activo y 2067 inactivos.

5. __Unión__ de los dos dataframes por la columna Loyalty Number, con outer merge para no perfer nada de información.

6. Guardar el nuevo dataframe como un nuevos csv llamdado __datos_completos__.


## 3. Visualizaciones

Nos importamos las librerías necesarias y creamos gráficas para responder a las siguientes preguntas:

1. ¿Cómo se distribuye la cantidad de vuelos reservados por mes durante el año?
Podemos observar que en 2018 hay más reservas todos los meses y que se reservan más vuelo en los meses de verano y diciembre.

2. ¿Existe una relación entre la distancia de los vuelos y los puntos acumulados por los cliente?

3. ¿Cuál es la distribución de los clientes por provincia o estado?

4. ¿Cómo se compara el salario promedio entre los diferentes niveles educativos de los clientes?

5. ¿Cuál es la proporción de clientes con diferentes tipos de tarjetas de fidelidad?

6. ¿Cómo se distribuyen los clientes según su estado civil y género?