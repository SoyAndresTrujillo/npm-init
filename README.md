# Dependencias

npm install moment

npm install eslint --save-dev (-D) —> dependencia que solo va a ser utilizada en el entorno de desarollo

npm install react --save (-S) —> dependencia para ser llevada a produccion.

# Paquetes Globales

npm install -g
Ver lista de los paquetes

npm list
Ver lista de paquetes globlales

npm list -g

# Modificar dependencias

- Como ya teniamos instalado eslint instalado en dev, podemo decirle que ahora solo este de manera opcional:

<npm install eslint -o>

# Instalar dependencias simuladas

<npm install package-name —dry-run>

Con esto se simula la instalación pero sin agregar ningún paquete, si no hay ningún conflicto se procede a instalar de la manera convencional.

# Instalar versión especifica

npm install package-name@0.15.0 → Instalar la versión especifica de un paquete.
Si luego se quiere instalar la versión más reciente se usa npm install package-name@latest.

# Actualización de dependencias
Muchas veces tenemos proyectos o tenemos que trabajar con proyectos que hace mucho tiempo han estado sin actualizarse

- Babel es un Transpilador para entender javascript moderno y lo pasa al último estándar de ECMAScript.
- Eslintrc Analizan nuestro código para dar mejorar que debemos implementar.
- .prettierrc estandat para manejar sintaxis
- Package.lock.json y package.json nuestros archivos estándares.
- Package.json: este archivo base contiene la información de nuestra aplicación, algo muy parecido a un manual de lo que necesita la aplicación para funcionar de la forma correcta.

# Actualización de paquetes
<npm list> nos muestra todos los elementos que son parte del proyecto y los errores correspondientes si es el caso y no están instalados.

<npm install> procederá a instalar todas las dependencias del proyecto y podremos tener mensajes como dependencias vulneradas, de forma moderadas, altas o criticas (deben ser atendidas inmediatamente)

<npm outdate> nos mostrará cuales son las dependencias que necesitan o que pueden ser actualizadas porque han tenido alguna mejora.

<npm install react@latest> si esta dependencia usa otras y también están desactualizadas, nos informará y podemos proceder a realizar la actualización de la otra >npm i react-dom@latest

# Auditar tus dependencias
El comando npm audit muestra una descripción de las dependencias instaladas. Si se encuentran vulnerabilidades, se calculará el impacto al proyecto.

Si se requiere un informe más detallado en formato JSON (JavaScript Object Notation), utiliza el comando npm audit --json.

El comando npm audit fix proporciona una actualización de los paquetes, similar al comando npm update <paquete>.
El comando npm audit fix --force proporciona una actualización de los subpaquetes de cada paquete, en todos sus niveles de profundidad.

Si el problema persiste, es necesario actualizar el paquete a su última versión.

bash $ npm install <paquete>@latest

Solución de problemas
Cuando estés desarrollando un proyecto con NPM, puede que generes errores que no permitan seguir con tu trabajo.
Saber manejar los errores es fundamental para solucionarlos y seguir con tus tareas (y no entrar en pánico). Alguno de estos errores pueden ser:

- Errores en la configuración del archivo package.json
- Errores de dependencias en node_modules
- Errores del sistema operativo
- Configuración errónea de Git o GitHub
- Errores de escritura (typos)
- Errores que no estén ligados directamente a NPM
- Error de dependencias en node_modules

Existen situaciones en las que instalas una dependencia con una versión que no corresponde a la deseada. Esto ocurre porque NPM guarda en el caché una versión previamente instalada de un paquete, esto para mejorar los tiempos de instalación.

En esta situación, puedes utilizar los siguientes comandos, el primero para borrar el caché de NPM y el segundo para verificar si están eliminados correctamente.

bash $ npm cache clean --force $ npm cache verify.

# Cómo actualizar node_modules
🔥 Actualizar el directorio node_modules sirve para limpiar las dependencias que previamente estaban en el proyecto. También cuando existe algún archivo corrupto o una mala instalación.

🔥 Por lo tanto, debemos eliminar el directorio de node_modules y después ejecutar el comando npm install para instalar correctamente los paquetes. En ciertas situaciones, también es necesario eliminar el archivo package-lock.json.
.
Puedes utilizar el siguiente comando phoenix en el package.json para evitar escribir demasiado cada vez que lo necesites. Lo aprendí de Midudev. 🙌

package.json
```js
{
 "scripts": {
   "phoenix": "rm -f package-lock.json && rm -rf ./node_modules && npm install --no-fund --no-audit"
 }
}
```