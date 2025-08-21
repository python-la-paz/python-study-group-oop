<!-- .slide: data-background-image="../../content/psg-bg-dark.png" data-background-size="100%"-->
![Python La paz](../Logo.png) <!-- .element  hidden="true" -->

<br>
<br>
<br>

### Sesión  12
#### Buenas prácticas
#### Anotaciones, Documentación y Principios

---

#### VS Code

Abrimos el proyecto del Study Group

```bash
code psg-oop-2025
```

Creamos una carpeta llamada `sesion12` dentro del proyecto

```bash
mkdir sesion12
cd sesion12
```

Aquí guardaremos los ejemplos de la sesión


---

Python es uno de los lenguajes más populares y entre sus características
se encuentra la facilidad para escribir código.

El tipado dinámico de Python permite a los desarrolladores escribir código
rápido y flexible

---
Pero esto también puede llevar a errores difíciles de detectar
si no se tiene cuidado.

---
Una variable puede cambiar de tipo en cualquier momento, lo que puede causar
errores en tiempo de ejecución.

Desde la terminal interactiva de Python:

```python
def sumar(a, b):
    return a + b
x = 5  # x es un entero
y = 10  # y es un entero
print(sumar(x, y))  # Funciona correctamente
x = "5"  # x ahora es una cadena
print(sumar(x, y))  # Error en tiempo de ejecución: TypeError
```

```text
15
ERROR!
Traceback (most recent call last):
  File "<main.py>", line 4, in <module>
  File "<main.py>", line 2, in sumar
TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

---
Este tipo de errores puede ser difícil de detectar y corregir,
especialmente en proyectos grandes.

Para lo cual, en Python se ha introducido el concepto de "anotaciones de tipo"

---

#### Anotaciones

Python desde su versión 3.6 introdujo el concepto de "anotaciones de tipo"
que permiten a los desarrolladores especificar el tipo de datos esperado
para:

- Variables
- Parámetros de funciones
- Valores de retorno de funciones
- Atributos de clases

---

Esto ayuda a mejorar la legibilidad del código y a detectar errores
antes de que se ejecuten.

Además, los editores de código y herramientas de análisis estático
pueden utilizar estas anotaciones para proporcionar sugerencias y advertencias.

![Anotaciones de tipo](./img/annotation_01.png) <!-- .element width="50%"-->

---

Crearemos un archivo llamado `anotaciones.py` en la carpeta `sesion12`

```bash
touch anotaciones.py
```

---

#### Anotaciones en variables

Las anotaciones de tipo en variables se utilizan para indicar el tipo de datos
que se espera que contenga una variable.

```python
edad: int = 30  
nombre: str = "Jhon" 
altura: float = 1.75
activo: bool = True
print(type(edad))  # <class 'int'>
print(type(nombre))  # <class 'str'>
print(type(altura))  # <class 'float'>
print(type(activo))  # <class 'bool'>
```

Estas anotaciones no afectan el comportamiento del código,
pero proporcionan información adicional para los desarrolladores

---

De esta manera, podemos ver que la variable `edad` es un entero,
`nombre` es una cadena, `altura` es un flotante y `activo` es un booleano.

Esto ayuda a los desarrolladores a entender mejor el código
y a detectar errores antes de que se ejecuten.

---

#### Anotaciones en variables

También se pueden utilizar anotaciones de tipo para estructuras de datos donde
se incluyen los tipos de los elementos que contienen

En el caso de listas se utiliza la sintaxis `list[tipo]`:
Donde `tipo` es el tipo de los elementos que contiene la lista.

---

En el caso de diccionarios se utiliza la sintaxis `dict[clave_tipo, valor_tipo]`:
Donde `clave_tipo` es el tipo de las claves y `valor_tipo` es el tipo de los valores.

En el caso de tuplas se utiliza la sintaxis `tuple[tipo1, tipo2, ...]`:
Donde `tipo1`, `tipo2`, etc. son los tipos de los elementos que contiene la tupla.


---

```python
numeros: list[int] = []
nombres: dict[str, str] = {}  
tuplas: tuple[int, str] = ()
print(type(numeros))  # <class 'list'>
print(type(nombres))  # <class 'dict'>
print(type(tuplas))  # <class 'tuple'>
```

- `numeros`: lista de enteros
- `nombres`: diccionario con claves y valores de tipo cadena
- `tuplas` : tuplas de enteros y cadenas

---

Sin anotaciones:

![Sin anotaciones](./img/annotation_02.png) <!-- .element width="50%"-->

Con anotaciones:

![Con anotaciones](./img/annotation_03.png) <!-- .element width="50%"-->

---

#### Anotaciones en funciones

Se utilizan para indicar los tipos de datos que se espera que contengan los parámetros 
y el tipo de dato que se espera que retorne

Los parámetros de una función se anotan utilizando la sintaxis `parametro: tipo`
y el valor de retorno se anota utilizando la sintaxis `-> tipo` 

El tipo de retorno se coloca antes de los dos puntos `:`

---

Por ejemplo, si tenemos una función que suma dos números enteros

```python
def sumar(a: int, b: int) -> int:
    return a + b
```

En este ejemplo, la función `sumar` espera dos parámetros de tipo entero
y retorna un valor de tipo entero.

---

Sin anotaciones:

![Sin anotaciones](./img/annotation_04.png) <!-- .element width="40%"-->

Con anotaciones:

![Con anotaciones](./img/annotation_05.png) <!-- .element width="40%"-->

---

#### Anotaciones en funciones

También se pueden utilizar anotaciones de tipo para funciones que aceptan
parámetros de tipo genérico, como listas o diccionarios.

Por ejemplo, si tenemos una función que recibe una lista de enteros y 
retorna una lista de cuadrados de esos enteros

```python
def cuadrados(numeros: list[int]) -> list[int]:
    return [n ** 2 for n in numeros]
numeros = cuadrados([2,4,6])
print (numeros)
```

---

Las anotaciones nos ayudan a saber que la variable `numeros` es una lista de enteros

![Con anotaciones](./img/annotation_06.png) <!-- .element width="60%"-->

---

#### Anotaciones en clases

Las anotaciones de tipo también se pueden utilizar en clases para indicar
los tipos de datos de los atributos de una clase.

Por ejemplo, si tenemos una clase `Persona` con atributos de clase `especie`
y atributos de instancia `nombre` y `edad`

---

```python
class Persona:
    especie: str = "Humano"
    def __init__(self, nombre: str, edad: int):
        self.nombre: str = nombre
        self.edad: int = edad
```


La clase `Persona` tiene un atributo de clase `especie` de tipo cadena
con el valor por defecto "Humano"

Atributos de instancia `nombre` y `edad` de tipo cadena e entero

---

Con anotaciones:

![Con anotaciones](./img/annotation_07.png) <!-- .element width="50%"-->


---

Existe otro estilo de anotaciones usado mayormente en versiones anteriores a Python 3.8

utilizando el módulo `typing` y las clases `List`, `Dict`, `Tuple`, etc.


---

Por ejemplo, si tenemos una función que recibe una lista de enteros y retorna una lista de enteros

```python
from typing import List
def cuadrados(numeros: List[int]) -> List[int]:
    return [n ** 2 for n in numeros]
numeros = cuadrados([2, 4, 6])
print(numeros)
```

Actualmente, este estilo es menos común y se recomienda utilizar las anotaciones
directamente sin importar el módulo `typing`

---

Es importante recordar que las anotaciones de tipo en Python son opcionales
y no afectan el comportamiento del código en tiempo de ejecución.

---

Pero no es suficiente, también es importante documentar el código
para que se pueda entender fácilmente su propósito y funcionamiento.

---

#### Documentación

La documentación es una parte esencial del desarrollo de software
ya que ayuda a los desarrolladores a entender el propósito y funcionamiento del código.

En las clases podemos utilizar cadenas de documentación (docstrings)
para documentar el propósito de la clase, sus atributos y métodos.

---

La documentación se coloca entre comillas triples `"""` justo después de la definición de la clase
o del método.

Los editores de código y herramientas de análisis estático pueden utilizar
estas cadenas de documentación para proporcionar sugerencias de autocompletado y advertencias.

---
Creamos un archivo llamado `documentacion.py` en la carpeta `sesion12`

```bash
touch documentacion.py
```

---

#### Documentación en clases

Por ejemplo, si tenemos una clase `Persona` con un atributo `nombre` y un método `saludar`

```python
Sin documentación:

class Persona:
    def __init__(self, nombre: str):
        self.nombre: str = nombre
    def saludar(self):
        print(f"Hola, mi nombre es {self.nombre}")
jhon = Persona("Jhon")
jhon.saludar()
```


![Sin documentación I](./img/documentation_01.png) <!-- .element width="35%"-->
![Sin documentación II](./img/documentation_02.png) <!-- .element width="35%"-->

---

Con documentación:

```python
class Persona:
    """Clase que representa a una persona."""
    def __init__(self, nombre: str):
        """Inicializa una nueva instancia de la clase Persona.
        
        Args:
            nombre (str): El nombre de la persona.
        """
        self.nombre: str = nombre

    def saludar(self):
        """Imprime un saludo con el nombre de la persona."""
        print(f"Hola, mi nombre es {self.nombre}")
jhon = Persona("Jhon")
jhon.saludar()
```

---

![Con documentación I](./img/documentation_03.png) <!-- .element width="50%"-->

![Con documentación II](./img/documentation_04.png) <!-- .element width="50%"-->

---

Existen diferentes convenciones para escribir documentación en Python 
la [PEP 257](https://peps.python.org/pep-0257/) establece la base para las cadenas de documentación

Existen diferentes estilos de documentación, como el estilo Google, NumPy y reStructuredText (reST)

Donde cada uno tiene su propia sintaxis y convenciones

---

| Estilo                  | Uso típico                                   |
| ----------------------- | -------------------------------------------- |
| Google                  | Documentación de proyectos y bibliotecas     |
| NumPy                   | Documentación científica y técnica           |
| reStructuredText (reST) | Documentación profesional, grandes proyectos |


---

| Estilo | Ventajas                    | Desventajas                                      |
| ------ | --------------------------- | ------------------------------------------------ |
| Google | Fácil de leer y escribir    | Menos detallado para proyectos complejos         |
| NumPy  | Estructurado y detallado    | Puede ser más difícil de leer para principiantes |
| reST   | Muy detallado y profesional | Más complejo de escribir menos amigable          |

---

| Estilo | Legibilidad                                                                       |
| ------ | --------------------------------------------------------------------------------- |
| Google | Claro y conciso, fácil  para humanos                                              |
| NumPy  | Muy estructurado, detallado, generado por herramientas                            |
| reST   | Muy detallado, profesional, orientado a herramientas de documentación como Sphinx |


---

#### Estilo Google

Para documentar una función o método, se utiliza la siguiente sintaxis:

```python
def fibonacci(n: int) -> str:
    """Devuelve la secuencia de Fibonacci hasta el n-ésimo número.

    Args:
        n (int): El índice del número de Fibonacci a calcular.

    Returns:
        str: La secuencia de Fibonacci hasta el n-ésimo número.

    Raises:
        ValueError: Si n es negativo.

    Examples:
        >>> fibonacci(5)
        '0, 1, 1, 2, 3'
    """
    if n < 0:
        raise ValueError("El índice no puede ser negativo")
    fib = [0, 1]
    for i in range(2, n):
        fib.append(fib[i - 1] + fib[i - 2])
    return ', '.join(str(x) for x in fib[:n])
print (fibonacci(5))
```

---
El editor de código puede interpretar la documentación y proporcionar sugerencias de autocompletado

![Estilo Google](./img/documentation_05.png) <!-- .element width="50%"-->


---
#### Estilo NumPy

Para documentar una función o método, se utiliza la siguiente sintaxis:

```python
def fibonacci(n: int) -> str:
    """
    Devuelve la secuencia de Fibonacci hasta el n-ésimo número.

    Parameters
    ----------
    n : int
        El índice del número de Fibonacci a calcular.

    Returns
    -------
    str
        La secuencia de Fibonacci hasta el n-ésimo número.

    Raises
    ------
    ValueError
        Si n es negativo.

    Examples
    --------
    >>> fibonacci(5)
    '0, 1, 1, 2, 3'
    """
    if n < 0:
        raise ValueError("El índice no puede ser negativo")
    fib = [0, 1]
    for i in range(2, n):
        fib.append(fib[i - 1] + fib[i - 2])
    return ', '.join(str(x) for x in fib[:n])

print(fibonacci(5))
```

---
El editor de código puede interpretar la documentación y proporcionar sugerencias de autocompletado

![Estilo NumPy](./img/documentation_06.png) <!-- .element width="40%"-->

---
#### Estilo reStructuredText (reST)
Para documentar una función o método, se utiliza la siguiente sintaxis:

```python
def fibonacci(n: int) -> str:
    """
    Devuelve la secuencia de Fibonacci hasta el n-ésimo número.

    :param n: El índice del número de Fibonacci a calcular.
    :type n: int
    :return: La secuencia de Fibonacci hasta el n-ésimo número.
    :rtype: str
    :raises ValueError: Si n es negativo.
    :example:
        >>> fibonacci(5)
        '0, 1, 1, 2, 3'
    """
    if n < 0:
        raise ValueError("El índice no puede ser negativo")
    fib = [0, 1]
    for i in range(2, n):
        fib.append(fib[i - 1] + fib[i - 2])
    return ', '.join(str(x) for x in fib[:n])

print(fibonacci(5))
```

---
El editor de código puede interpretar la documentación y proporcionar sugerencias de autocompletado

![Estilo reST](./img/documentation_07.png) <!-- .element width="40%"-->

---

Elige un estilo de documentación y sé consistente en su uso a lo largo de tu código

Esto facilitará la lectura y comprensión del código para ti y para otros desarrolladores

---

#### Principios de desarrollo

Los principios de desarrollo son un conjunto de buenas prácticas
que ayudan a los desarrolladores a escribir código limpio, mantenible y escalable.

Al igual que los patrones de diseño, los principios de desarrollo
proporcionan soluciones a problemas comunes en el desarrollo de software.

---
Algunos de los principios más importantes son:

- KISS (Keep It Simple, Stupid)
- DRY (Don't Repeat Yourself)
- YAGNI (You Aren't Gonna Need It)




---
<!-- .slide: data-background-image="../../content/psg-bg-dark.png" data-background-size="100%"-->

<br>
<br>
<br>
<br>
<br>

[![GitHub](../../content/github_logo.png) <!-- .element width="20%"-->](https://github.com/python-la-paz/python-study-group-oop/content/sesion01)

Repositorio de la Sesión

---
<!--.slide: data-visibility="hidden"-->
## Bibliografía y Referencias

- [Object Oriented Analysis](https://www.gyata.ai/es/object-oriented-programming/object-oriented-analysis)
- [DDOO Unidad 1](https://dmd.unadmexico.mx/contenidos/DCEIT/BLOQUE1/DS/02/DDOO/U1/descargables/DDOO_Unidad_1.pdf)
- [Programación procedural VS orientada a objetos](https://programacionpro.com/programacion-procedural-vs-orientada-a-objetos-diferencias-y-similitudes/)
- [Python OOP](https://www.learnpython.org/en/Classes_and_Objects)
- [Atributos de clase](https://oregoom.com/python/atributos-clase/)
- [Diagrama de clases](https://diagramasuml.com/diagrama-de-clases/)
- [Guía PEP 8](https://peps.python.org/pep-0008/#class-names)
- [Mermaid Charts](https://www.mermaidchart.com/play)
- [Draw.io](https://app.diagrams.net/)
- [Python 3 Object-oriented Programming, Second Edition, Dusty PhillipsDusty Phillips](https://github.com/PacktPublishing/Python-3-Object-Oriented-Programming-Second-Edition)
- [Objetos en programación](https://ebac.mx/blog/objeto-en-programacion)
- [Enfoque orientado a objetos](https://1library.co/article/enfoque-orientado-a-objetos-base-te%C3%B3rica.qvld461y)
- [OOAD](https://www.tutorialspoint.com/object_oriented_analysis_design/ooad_object_oriented_analysis.htm)

https://ellibrodepython.com/function-annotations
https://docs.python.org/es/3/howto/annotations.html
https://pywombat.com/articles/python-annotation
https://peps.python.org/pep-0484/
https://peps.python.org/pep-0585/#parameters-to-generics-are-available-at-runtime