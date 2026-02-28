---
sidebar_position: 1
---

# Configure cache

Con cada actualización, podemos encontrarnos con el problema de que no se carguen las modificaciones desde el cliente. Para evitar que el navegador cargue los ficheros desde la caché, debemos hacer lo siguiente:

## Configuación Tomcat

En nuestro servidor Tomcat, modificar el fichero de configuración web.xml. Se encuentra en la carpeta conf, en el directorio del Tomcat.

Aquí, debemos añadir el siguiente código:

```
<!-- ================== Built In Filter Definitions ===================== -->
    <filter>
        <filter-name>ExpiresFilter</filter-name>
        <filter-class>org.apache.catalina.filters.ExpiresFilter</filter-class>
        <init-param> 
            <param-name>ExpiresDefault</param-name>
            <param-value>modification plus 0 minutes</param-value>
        </init-param>
        </filter>

    <filter-mapping>
        <filter-name>ExpiresFilter</filter-name> 
        <url-pattern>/*</url-pattern> 
        <dispatcher>REQUEST</dispatcher>
    </filter-mapping>
```

Por último, en el fichero .html principal debemos añadir el siguiente código:

```
   <meta http-equiv="Cache-Control" content="no-store, no-cache, must-revalidate, max-age=0, post-check=0, pre-check=0" />
   <meta http-equiv="Pragma" content="no-cache" />
   <meta http-equiv="Expires" content="0" />
```
