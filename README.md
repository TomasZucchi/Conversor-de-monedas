<img  alt="exchangeimg" width="200px" height="200px" align="right" src="https://images.vexels.com/media/users/3/146882/isolated/preview/7525685ed67fa782b7d851273e1264c7-cambio-de-divisas.png" >

## Conversor de monedas

Proyecto para el programa ONE-Backend. La app está desarrollada en Java 17 para realizar la conversión de distintas monedas. Se basa en el consumo de la API de [ExchangeRate-API](https://www.exchangerate-api.com/), de este modo esta app se alimenta de los listados de países y de la tasa de cambio entre dos monedas dadas.

`Si deseas probar la aplicación visita el apartado de preparación del ambiente! :3`

## Tabla de contenidos

- [Funcionalidades de la app](#funcionalidades-de-la-app)

- [Preparación del ambiente](#preparacion-del-ambiente)

### Funcionalidades de la app

En estas app te encuentras seis opciones (La ultima sale como 7 por propositos de la app misma, fue a proposito jeje):

    1. [Hacer conversión de moneda](#hacer-conversion-de-moneda).
    2. Ver listado actual de monedas.
    3. Agregar una moneda al listado.
    4. Eliminar una moneda del listado.
    5. Ver tu historial de conversión de monedas.
    7. Salir
    
Te dejo aquí los atajos para que puedas verlas de forma más rápida:

- [1. Hacer conversión de moneda](#hacer-conversion-de-moneda)
- [2. Ver listado actual de monedas](#ver-el-listado-actual-de-monedas)
- [3. Agregar una moneda al listado](#agregar-una-moneda-al-listado)
- [4. Eliminar una moneda del listado](#eliminar-una-moneda-del-listado)
- [5. Ver tu historial de conversión de monedas](#ver-tu-historial-de-conversion-de-monedas)
    
La app funciona con un listado de monedas para facilitar la interacción y ampliar las posibilidades de conversión de monedas. Este listado puede ser modificado a gusto del usuario.

Inicialmente se ejecuta un listado por defecto:

    1. ARS: Peso argentino.
    2. BOB: Boliviano boliviano.
    3. BRL: Real brasileño.
    4. CLP: Peso chileno.
    5. COP: Peso colombiano.
    6. USD: Dolar estadounidense

A continuación exploramos cada opción del menú:

### Hacer conversion de moneda

- Al seleccionar esta opción primero se mostrará el listado actual de monedas:



- Posterior a ello te pedirá que selecciones alguno de ellos como moneda principal (es decir el baseCode), en este ejemplo ponemos 5 que es el peso Colombiano:




- Luego, te pedirá que selecciones una segunda moneda de la lista, esta será la moneda a la cual deseas convertir tu monto (es decir la targetCode), en este ejemplo ponemos 6 que es el dolar estadounidense:


- Finalmente, te pide que ingreses el monto que deseas convertir, para este ejemplo pondremos lo que cuestan unas papas fritas en Colombia :Q



- Una vez ingresas el monto te muestra la conversión con todos los datos que ingresaste. (En efecto, unas papas fritas solo cuestan 4 dolares con 61 centavos OwO)


- Luego de mostrar tu conversión, te preguntará si deseas realizar otra conversión (es decir continuar en la op 1) o regresar a menu inicial.



Es importante mencionar que para el funcionamiento de esta opción se hace una peticion de tipo GET a la API exchange la cual estamos consumiendo, la url ejemplo de la API es: `https://v6.exchangerate-api.com/v6/YOUR-API-KEY/pair/baseCode/targetCode`


### Ver el listado actual de monedas

Dado que la lista es modificable, quizá quieras ver tu lista actual, una vez ingreses la opción 2 en el menú te mostrará la lista actualizada que tienes disponible


Finalmente, te pide que ingreses cualquier caracter para regresar al menu



### Agregar una moneda al listado

- Al seleccionar esta opción, primero te mostrará una lista de países que puedes añadir a tu lista:

- Te solicita que selecciones el número del país que desees añadir, en este ejemplo seleccionamos el 148 que es el Peso uruguayo

- Se añade tu país a la lista y te muestra la lista actualizada

- Finalmente, te da la opción de seguir añadiendo países o regresar al menu

Es importante denotar que aquí no puedes añadir países que ya esten en tu lista, la misma app te avisará cuando lo intentes y te solicitará que ingreses uno valido, en este ejemplo utilizamos el 147 que es el USD que ya se encuentra en la lista:

Tambien es importante comentar que esta opción toma el listado de países de la API exchange haciendo un llamado de tipo GET a su url especifica de los códigos `https://v6.exchangerate-api.com/v6/YOUR-API-KEY/codes`

Este llamado retornada un Json con todos los paises que soporta la API


(La app de fondo guarda la lista de paises para evitar hacer más llamados a la API, es decir, luego de mostrar la lista por primer vez ya no hace llamados a la API, sino que muestra una lista que guarda la app misma)

### Eliminar una moneda del listado

- Al seleccionar esta opción te mostrará el listado actual para que puedas decidir cual eliminar, en este ejemplo seleccionamos 9 para eliminar el YER


- Una vez selecciones el número, lo eliminará y te preguntará si deseas continuar eliminando países de la lista


- Si miramos la opción dos, nos saldrá el listado actualizado


Aquí no hacemos peticiones a la API dado que se interactua puramente con las listas locales de la app; sin embargo, la app no te deja eliminar todos los países. Una vez tengas solo dos no puedes seguir eliminando, dado que se necesitan al menos dos para hacer una conversión de moneda.


### Ver tu historial de conversion de monedas

Al seleccionar esta opción te saldrá tu historial de todas las conversiones de moneda que haz hecho, organizadas desde la más antigua hasta la más reciente mostrandote los datos relativos a la conversión que realizaste en su momento.

Finalmente, te solicita que ingreses un caracter cualquiera para regresar al menu:


### Preparacion del ambiente

Para la ejecución de la app es necesario seguir los pasos que te presento a continuación para evitar errores de compilación y/o ejecución:

#### 1. Configurar la variable de entorno

- Primero debes solicitar tu API-Key en la API de [ExchangeRate-API](https://www.exchangerate-api.com/), es completamente gratuito y solo debes añadir tu mail

- Luego, debes descargar este proyecto y abrirlo en tu IDE de preferencia :) `(recomiendo hacerlo desde Intellij para configurar todo más facil jeje)`.
- Nos ubicamos en el archivo principal `src/Main.java`, damos click derecho, nos ubicamos en `More run/ debug` y finalmente en `Modify run configuration...`

- Finalmente, añades tu api-key en el apartado de variables de entorno con el nombre de la variable: `EXCHANGE-API-KEY` y seleccionas `OK`.


