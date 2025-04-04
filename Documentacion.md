# Documentación de la exploración básica de los datos.

## 1. Carga de datos y análisis básico exploratorio con primeras impresiones.
- Hay dos df que se pueden unir por 'Loyalty number', pero al poner 'index_col=0' convierte esta columna, la primera en el índice de cada df, por eso no sale en info como columna. Si se quiere volver a poner como columna: df_vuelos.reset_index(inplace=True)
- Parece que no hay nulos.

    Posibles pasos:
    - Búsqueda de nulos.
    - Búsqueda de duplicados.
    - Cambiar tipo de datos: points accumulated float > int
    - Búsqueda de datos negativos.
    - Bucle para ver los datos únicos.
    - Ver describe.
    - Convertir texto a minúscula y eliminar espacios.
    - Corregir erratas si las hay.

    1. En el df_clientes hay nulos en Salary, Cancellation Year y Cancellation Month.
        En el df_ vuelos no hay nulos.
        Se puede hacer una __columna nueva de cuales están activos e inactivos por los nulos en cancellation__, creo que puede ser muy interesante para sacar posibles datos en el futuro de su actividad antes de cancelar o por qué han cancelado.