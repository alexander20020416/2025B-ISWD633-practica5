
**Aprendizajes logrados:**

Antes de realizar esta práctica, mi conocimiento sobre Docker era bastante básico. Sabía que existían los contenedores pero no tenía claro cómo funcionaban en aplicaciones reales ni cómo se conectaban entre sí. Esta práctica me permitió entender varios conceptos fundamentales que van a ser muy útiles en mi formación como desarrollador.

Lo primero que aprendí fue el uso de Docker Compose. Antes pensaba que había que crear cada contenedor manualmente con comandos largos y complicados, pero ahora entiendo que con un archivo YAML puedo definir toda la arquitectura de mi aplicación de manera organizada. Es mucho más práctico tener todo en un solo archivo que puedo versionar y compartir con mi equipo.

Otro aprendizaje importante fue sobre las redes en Docker. Al principio no entendía cómo los contenedores se comunicaban entre sí, pero al trabajar con WordPress y MySQL, y luego con SonarQube y PostgreSQL, me quedó claro que al estar en la misma red bridge pueden referenciarse directamente por el nombre del servicio. Esto simplifica muchísimo las configuraciones.

El tema de los volúmenes también fue revelador. Ahora comprendo por qué es importante persistir los datos fuera del contenedor, porque si no, cada vez que elimino un contenedor pierdo toda la información. Los volúmenes nombrados son la solución para mantener los datos seguros incluso si recreo los contenedores.

Los healthchecks fueron algo nuevo para mí. Me parece una práctica muy profesional poder verificar automáticamente que un servicio está funcionando correctamente antes de iniciar servicios que dependen de él. Esto evita muchos errores y hace que el despliegue sea más confiable.

En cuanto a problemas que enfrenté, el más significativo fue el conflicto de puertos con Jenkins. Al principio intenté usar el puerto 8080 para WordPress, pero resultó que Jenkins ya lo estaba ocupando. La solución fue simplemente cambiar el puerto en el archivo compose.yaml al 8081. Esto me enseñó la importancia de revisar qué puertos están en uso antes de configurar nuevos servicios.

Otro problema menor fue cuando copié el comando en CMD en lugar de PowerShell. Aprendí que hay diferencias importantes entre las dos terminales de Windows y que ciertos comandos solo funcionan en PowerShell. Ahora sé identificar cuál terminal estoy usando y qué comandos son apropiados para cada una.

Esta práctica me dejó con habilidades concretas que voy a usar en proyectos reales: sé configurar entornos de desarrollo completos con bases de datos, puedo levantar herramientas de análisis de código como SonarQube, y entiendo cómo orquestar múltiples servicios de manera eficiente. Todo esto me hace sentir más preparado para trabajar en ambientes profesionales donde Docker es el estándar.
