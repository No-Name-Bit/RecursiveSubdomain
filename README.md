
#Subdomain & Security Scanner 🕵️‍♂️

Una herramienta de código abierto para la enumeración de subdominios y el escaneo de encabezados de seguridad web.

##Descripción
Este script de Python automatiza dos tareas clave en la fase de reconocimiento de una prueba de penetración:

**Búsqueda Pasiva de Subdominios**: Utiliza las bases de datos públicas de Transparencia de Certificados (CT logs) a través de la API de crt.sh para encontrar subdominios de forma recursiva, sin necesidad de diccionarios o de enviar peticiones ruidosas.

**Verificador de Encabezados de Seguridad**: Analiza una URL para determinar si tiene implementados encabezados de seguridad críticos como HSTS, CSP y X-Frame-Options.

**Verificación de Estado**: Opcionalmente, puede comprobar el estado HTTP (código de respuesta) de todos los subdominios encontrados para verificar si están activos.

**Características**
Búsqueda Recursiva: Descubre subdominios y sus subdominios anidados.

**Modo Silencioso**: No genera tráfico directo a los dominios objetivo para la enumeración, lo que lo hace ideal para el reconocimiento sigiloso.

**Soporte para Tor**: Utiliza el proxy SOCKS5 de Tor para anonimizar las peticiones a las bases de datos públicas.

**Exportación de Resultados**: Guarda las listas de subdominios y los resultados del estado en archivos de texto para su posterior análisis.

**Manejo de Errores**: Captura de errores de conexión, timeouts y excepciones de teclado (Ctrl+C) para una ejecución estable y controlada.

Instalación
Clona este repositorio en tu máquina local:

````Bash
git clone https://github.com/no-name-bit/RecursiveSubdomain.git
cd RecursiveSubdomain
````

Instala las dependencias de Python. Si planeas usar la función de Tor, asegúrate de tener el Tor Browser o el Tor Daemon en ejecución en tu sistema.

````Bash
pip install -r requirements.txt
````

Nota: El archivo requirements.txt contiene las librerías requests y PySocks.

Uso
La herramienta se ejecuta desde la línea de comandos con diferentes argumentos según la tarea que desees realizar.

##1. Búsqueda de Subdominios y Análisis de Estado
   
Sintaxis:

````Bash
python3 scan_tool.py -d <dominio> -o <archivo_salida> [--tor]
````
Ejemplo:

````Bash
python3 scan_tool.py -d tu-dominio.com -o subdominios_encontrados.txt
````

Al finalizar, el script te preguntará si deseas analizar el estado de los subdominios encontrados.

##2. Verificación de Encabezados de Seguridad
Sintaxis:

````Bash
python3 scan_tool.py -u <url> [--tor]
````
Ejemplo:

````Bash
python3 scan_tool.py -u https://www.ejemplo.com
````

Puedes omitir la opción --tor si no deseas usar Tor.

###Futuras Mejoras

En el futuro, me gustaría añadir más fuentes de datos para que la recopilación y el filtrado sean más óptimos.

###Contribuciones

Las contribuciones son bienvenidas. Si encuentras un error o tienes una idea para una nueva funcionalidad, no dudes en abrir un issue o enviar un pull request.

###Licencia

Este proyecto está bajo la licencia MIT.
