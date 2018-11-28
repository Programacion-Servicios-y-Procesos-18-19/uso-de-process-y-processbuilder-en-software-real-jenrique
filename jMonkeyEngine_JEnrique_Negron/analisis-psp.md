##¿De qué forma se crea el proceso hijo? comando de invocación, parámetros…

[Crea el proceso hijo](https://github.com/Programacion-Servicios-y-Procesos-18-19/uso-de-process-y-processbuilder-en-software-real-jenrique/blob/731bf71f11c3b944f33acb9c262f878715efa036/jMonkeyEngine_JEnrique_Negron/codigo%20analizado.txt#L5) enviándole como parámetro al constructor de ProcessBuilder el comando que quiere ejecutar junto con su parámetro.
En este caso el proceso hijo ejecutará el **comando “cgc --version”**.

##¿Se conecta el proceso padre a los flujos de entrada, salida o errores del proceso hijo?

Sí, mediante un [objeto **Scanner**](https://github.com/Programacion-Servicios-y-Procesos-18-19/uso-de-process-y-processbuilder-en-software-real-jenrique/blob/731bf71f11c3b944f33acb9c262f878715efa036/jMonkeyEngine_JEnrique_Negron/codigo%20analizado.txt#L11), que a su vez se compone del flujo de errores del proceso hijo.

##¿Se emplea algún mecanismo de comunicación entre procesos?

Con el objeto Scanner, lee la primera línea del flujo de errores del proceso hijo y lo guarda en un String llamado “ln”

##¿Espera el padre al fin de la ejecución del hijo? ¿Se realiza alguna acción con su valor devuelto?

Sí, ejecuta el [método **waitFor()**](https://github.com/Programacion-Servicios-y-Procesos-18-19/uso-de-process-y-processbuilder-en-software-real-jenrique/blob/731bf71f11c3b944f33acb9c262f878715efa036/jMonkeyEngine_JEnrique_Negron/codigo%20analizado.txt#L18).
Luego guarda en un String llamado “versionNumber” el resultado de formatear el String “ln” con el método split.
Por último devuelve el valor del String “versionNumber” pero eliminando el último carácter (posiblemente porque sea un espacio en blanco).

##¿En qué contexto se utilizan los ejemplos encontrados? ¿En qué módulo o clase de la aplicación? (puede ser útil consultar la documentación del proyecto en el propio github, en su página oficial...)

    Utilizan esta clase cuando se emplea una aplicación de terceros llamada “NVIDIA Cg Toolkit”. La clase en la que se encuentra el ProcessBuilder está ubicada en el módulo de “Tools”

##¿Para qué fin se crean los procesos? (investiga razonablemente y en lo posible da una respuesta documentada, o si no es posible una respuesta intuitiva)

Utilizan este proceso para devolver la versión instalada de NVIDIA Cg Toolkit.
Esto podría ser utilizado para verificar que se está usando la versión correcta.

