# Documentación de la exploración básica de los datos.

## 1. Carga de datos y análisis básico exploratorio con primeras impresiones.
- Hay dos df que se pueden unir por 'Loyalty number', pero al poner 'index_col=0' convierte esta columna, la primera en el índice de cada df, por eso no sale en info como columna. Si se quiere volver a poner como columna: df_vuelos.reset_index(inplace=True)
- Parece que no hay nulos.

    Posibles pasos:
    - Búsqueda de nulos.
    - Búsqueda de duplicados.
    - Cambiar tipo de datos. **
    - Búsqueda de datos negativos. **
    - Bucle para ver los datos únicos.
    - Ver describe.
    - Convertir texto a minúscula y eliminar espacios.
    - Corregir erratas si las hay.

    1. En el df_clientes hay nulos en Salary, Cancellation Year y Cancellation Month.
        - En el df_ vuelos no hay nulos.
        - Se puede hacer una __columna nueva de cuales están activos e inactivos por los nulos en cancellation__, creo que puede ser muy interesante para sacar posibles datos en el futuro de su actividad antes de cancelar o por qué han cancelado.

    2. Hacemos un bucle para buscar los valores únicos y así ver inconsistencias o errores tipográficos.
        - En df_clientes __Country__ solo tiene un valor único, se podría eliminar la columna si la empresa solo tuviera clientes de ese país, pero puede que busque ampliar los países.
        - No hay errores tipográficos en ninguno de los dos.
        - Hay que cambiar varios float a int en los dos df: points accumulated (vuelos) y cancellation month/year (clientes).

    3. Hacemos otro para ver si hay valores negativos, ya que no se ven todos los únicos en algunas columnas.
        - En df_vuelos no hay valores negativos.
        - En df_clientes hay 20 valores negativos en Salary, se pueden cambiar a positivos ya que parece un error al meter los datos.

    4. Buscamos duplicados.
        - En clientes no hay.
        - En vuelos hay 228705: entendemos que cada cliente vuela varias veces, por eso hay varios registros del mismo cliente.

## 2. Limpieza y cambios

1. FLOAT a INT: points accumulated (vuelos) y cancellation month/year (clientes). Este último hay que tener en cuenta que tienen NaN, por lo que habrá que poner Int64 para mantenerlos.
