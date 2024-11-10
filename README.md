<div align='center'>
  <img height="60" src="https://upload.wikimedia.org/wikipedia/commons/4/4c/Typescript_logo_2020.svg">
  <h1>Resumen y detalles de TypeScript</h1>

  <sup>Deja tu :star: si te gusta el proyecto.</sup>

</div>

## Índice

- [Índice](#índice)
    - [**¿Qué es TypeScript?**](#qué-es-typescript)
    - [**Ventajas de usar TypeScript**](#ventajas-de-usar-typescript)
    - [**Tipos de datos**](#tipos-de-datos)
    - [**Declarar tipos en TypeScript**](#declarar-tipos-en-typescript)


#### **¿Qué es TypeScript?**
TypeScript es un lenguaje de programación desarrollado por Microsoft que se basa en JavaScript, añadiendo características adicionales como el tipado estático y la orientación a objetos.
Es un superconjunto de JavaScript, lo que significa que cualquier código JavaScript válido también es válido en TypeScript.

Algunas de las principales características de TypeScript incluyen:

1. **Tipado estático**: Permite definir tipos para variables y funciones, lo que ayuda a detectar errores en tiempo de desarrollo.
2. **Orientación a objetos**: Añade soporte para clases y módulos, facilitando la organización del código.
3. **Compatibilidad con JavaScript**: Puedes usar cualquier código JavaScript existente en un proyecto TypeScript.
4. **Mejoras en el desarrollo**: Herramientas como IntelliSense en editores de código proporcionan autocompletado y documentación en línea más precisos.

**[⬆ Volver a índice](#índice)**

---

#### **Ventajas de usar TypeScript**

1. **Tipado estático**: TypeScript permite definir tipos para tus variables, funciones y componentes, lo que ayuda a detectar errores en <u>tiempo de desarrollo</u> en lugar de en <u>tiempo de ejecución</u>. Esto puede reducir significativamente los bugs y mejorar la calidad del código.

2. **Mejor autocompletado y documentación**: Los editores de código como Visual Studio Code pueden proporcionar autocompletado y documentación en línea más precisos cuando usas TypeScript, lo que acelera el desarrollo y reduce errores.

3. **Refactorización más segura**: Con TypeScript, puedes refactorizar tu código con mayor confianza, ya que el sistema de tipos te ayudará a identificar rápidamente las áreas afectadas por los cambios.

4. **Mantenimiento a largo plazo**: El código tipado es generalmente más fácil de entender y mantener, especialmente en proyectos grandes o cuando trabajas en equipo. Los tipos actúan como una forma de documentación que puede ser muy útil para nuevos desarrolladores que se unan al proyecto.

5. **Detección temprana de errores**: Al compilar el código, TypeScript puede detectar errores que JavaScript no detectaría hasta que el código se ejecute, lo que puede ahorrar tiempo y esfuerzo en la depuración.

Estas ventajas hacen que TypeScript sea una excelente opción para proyectos de React, especialmente si buscas mejorar la robustez y mantenibilidad de tu código. ¿Te gustaría saber más sobre cómo empezar a usar TypeScript en un proyecto de React?

**[⬆ Volver a índice](#índice)**

---

#### **Tipos de datos**
En JavaScript, hay seis tipos de datos básicos que se pueden dividir en tres categorías principales:

- **Primitivos**. **String, Number y Boolean** son tipos de datos <u>**primitivos**</u>.

- **Compuestos**. **Object, Array y Function** (que son todos tipos de objetos) son tipos de datos <u>**compuestos**</u>.

- **Especiales**. Mientras que **Undefined** y **Null** son tipos de datos <u>**especiales**</u>.

**[⬆ Volver a índice](#índice)**

---

#### **Declarar tipos en TypeScript**
 - **inferencia**, en la que no se declara un tipo en absoluto, pero TypeScript lo infiere (adivina) por usted.
 ```js
 let helloWorld = "Hello World";
 ```
 - **Definición de tipos**:  A grega dos puntos y su tipo a la derecha de lo que sea que estés declarando 
  ```js
  let myName: string = "Germán";
  ```
  - **Interfaz**: Para trabajar con **objetos** Se parece mucho a un objeto JavaScript.
    - Usamos la palabra clave **interface**.
    - No tenemos un signo igual o comas.
    - En cada clave tenemos su tipo de datos en lugar de su valor.
```js
interface User {
  name: string;
  id: number;
}

const user: User = {
  name: "Hayes",
  id: 0,
};
```

    - Puede utilizar interfaces para anotar parámetros y devolver valores a las funciones:

```js
function deleteUser(user: User) {
  // ...
}
 
function getAdminUser(): User {
  //...
}
```
Hay un pequeño conjunto de tipos primitivos disponibles en JavaScript: ``boolean``, ``bigint*``, ``null``, ``number``, ``string``, ``symbol**``, y ``undefined``, que puedes usar en una interfaz. TypeScript amplía esta lista con algunos más, como any (permite cualquier cosa), unknown (asegura que alguien que use este tipo declare cuál es el tipo), never (no es posible que este tipo pueda ocurrir), y void (una función que devuelve indefinido o no tiene valor de retorno).

- <small>**bigint***: Permite representar enteros grandes y realizar operaciones con ellos sin perder precisión. Se define agregando una n al final de un número entero </small>
- <small>**symbol****: Para crear identificadores únicos. Cada valor de Symbol es único y se utiliza comúnmente como clave de propiedades en objetos. Son útiles para evitar conflictos de nombres en las propiedades, especialmente cuando trabajamos con librerías o módulos de terceros.
  ```js
  // Crear símbolos
  let sym1 = Symbol('id');
  let sym2 = Symbol('id');

  console.log(sym1 === sym2); // Imprime: false, ya que cada símbolo es único

  // Usar símbolos como claves de propiedades en un objeto
  let user = {
    [sym1]: '12345', // clave única en el objeto
    name: 'John Doe'
  };

  console.log(user[sym1]); // Imprime: 12345
  ```

  Uso común de Symbol:

  Los Symbol pueden ser útiles para definir propiedades "ocultas" en objetos que no colisionen con otras claves.
Existen símbolos globales predefinidos en JavaScript, como Symbol.iterator, Symbol.asyncIterator, etc., que se utilizan en patrones de iteración y otras funcionalidades avanzadas del lenguaje.
</small>

- **Tipos de composición** Hay dos formas populares de hacerlo: uniones y genéricos.
  - **Unión**:  Un caso de uso popular para los tipos de unión es describir el conjunto de literales o que puede ser un valor: string number
    ```js
    type WindowStates = "open" | "closed" | "minimized";
    type LockStates = "locked" | "unlocked";
    type PositiveOddNumbersUnderTen = 1 | 3 | 5 | 7 | 9;
    ```
    Las uniones también proporcionan una forma de manejar diferentes tipos. Por ejemplo, puede tener una función que tome un o un :array string
    ```js
    function getLength(obj: string | string[]) {
      return obj.length;
    }
    ```
  - **Genéricos**: Proporcionan variables a los tipos.  Un ejemplo común es una matriz. Una matriz sin genéricos: **type StringArray = []**; podría contener cualquier cosa. Una matriz con genéricos: **type StringArray = Array<string>**; puede describir los valores que contiene la matriz.
    ```js
    type StringArray = Array<string>;
    type NumberArray = Array<number>;
    type ObjectWithNameArray = Array<{ name: string }>;
    ```
ME HE QUEDADO AQUÍ:
https://www.freecodecamp.org/espanol/news/como-usar-typescript-en-aplicaciones-react/
https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html


https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html
