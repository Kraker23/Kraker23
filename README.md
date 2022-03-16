Repositorio original: [ryanmcdermott/clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript)

# clean-code-javascript 

## Contenido
  1. [Introducción](#introducción)
  2. [Variables](#variables)
  3. [Funciones](#funciones)
  4. [Objetos y estructuras de data](#objetos-y-estructuras-de-data)
  5. [Clases](#clases)
  6. [SOLID](#solid)
  7. [Pruebas](#pruebas)
  8. [Concurrencia](#concurrencia)
  9. [Resolver los errores](#resolver-los-errores)
  10. [Formatear](#formatear)
  11. [Comentarios](#comentarios)

## Introducción

![Imagen gracioso de la estimación de la calidad de software como una cifra 
de cuantos expletivos que uno puede gritar al leer programas](http://www.osnews.com/images/comics/wtfm.jpg)

Los principios de la ingeniería de software, del libro de Robert C. Martin [*Clean Code*](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882), adaptado para JavaScript. Esta no es una guía de estilo, en cambio, es una guía para crear software que sea reutilizable, comprensible y que se pueda mejorar con el tiempo.

No hay que seguir tan estrictamente todos los principios en este libro, y vale la pena mencionar que hacia muchos de ellos habrá controversia en cuanto al consentimiento. Estas son reflexiones hechas después de muchos años de experiencia colectiva de los autores de *Clean Code*.

Nuestra obra de ingeniería de software lleva poco más que 50 años como negocio, y aún estamos aprendiendo. Cuando la arquitectura de software llegue a ser tan vieja como la arquitectura en sí misma, quizás tengamos reglas más estrictas para seguir. Hasta entonces, dejemos que estas guías sirvan como ejemplo para medir la calidad del código en JavaScript que tú y tu equipo producen.

Una cosa más: saber esto no te hará un mejor ingeniero inmediatamente, y tampoco trabajar con estas herramientas durante muchos años garantiza que nunca te equivocarás. Cualquier código empieza primero como un borrador, como arcilla mojada moldeándose en su forma final. Por último, arreglamos las imperfecciones cuando lo repasamos con nuestros compañeros de trabajo. No seas tan duro contigo mismo por los borradores iniciales que aún necesitan mejorar. ¡Trabaja más duro para mejorar el programa!

## **Variables**
### Utiliza nombres significativos y pronunciables para las variables

**Mal hecho:**
```javascript
const yyyymmdstr = moment().format('YYYY/MM/DD');
```

**Bien hecho:**
```javascript
const fechaActual = moment().format('YYYY/MM/DD');
```
**[⬆ vuelve hasta arriba](#contenido)**

### Utiliza el vocabulario igual para las variables del mismo tipo 

**Mal hecho:**
```javascript
conseguirInfoUsuario();
conseguirDataDelCliente();
conseguirRecordDelCliente();
```

**Bien hecho:**
```javascript
conseguirUsuario();
```
**[⬆ vuelve hasta arriba](#contenido)**

### Utiliza nombres buscables 

Nosotros leemos mucho más código que jamás escribiremos. Es importante que el código que escribimos sea legible y buscable. Cuando faltamos nombrar a las variables de manera buscable y legible, acabamos confundiendo a nuestros lectores. Echa un vistazo a las herramientas para ayudarte: [buddy.js](https://github.com/danielstjules/buddy.js) y
[ESLint](https://github.com/eslint/eslint/blob/660e0918933e6e7fede26bc675a0763a6b357c94/docs/rules/no-magic-numbers.md)

**Mal hecho:**
```javascript
// Para qué rayos sirve 86400000? 
setTimeout(hastaLaInfinidadYMasAlla, 86400000);
```

**Bien hecho:**
```javascript
// Decláralos como variables globales de 'const'.
const MILISEGUNDOS_EN_UN_DIA = 8640000;
setTimeout(hastaLaInfinidadYMasAlla, MILISEGUNDOS_EN_UN_DIA);
```
**[⬆ vuelve hasta arriba](#contenido)**

### Utiliza variables explicativas
**Mal hecho:**
```javascript
const direccion = 'One Infinite Loop, Cupertino 95014';
const codigoPostalRegex = /^[^,\\]+[,\\\s]+(.+?)\s*(\d{5})?$/;
saveCityZipCode(direccion.match(codigoPostalRegex)[1], direccion.match(codigoPostalRegex)[2]);
```
