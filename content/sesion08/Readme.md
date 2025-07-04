<!-- .slide: data-background-image="../../content/psg-bg-dark.png" data-background-size="100%"-->
![Python La paz](../Logo.png) <!-- .element  hidden="true" -->

<br>
<br>
<br>

### Sesión  08
#### Dunder Methods
#### Personalización y control del comportamiento

---

<!-- Que son los dunder methods
beneficios y usos reales
Como se declaran y su notacion
Metodos de inicializacion y destruccion
Metodos de representacion y conversion
Metodos de comparacion
Operadores aritmeticos
Operadores de comparacion
Metodos de coleccion -->

---

---

#### VS Code

Abrimos el proyecto del Study Group

```bash
code psg-oop-2025
```

Creamos una carpeta llamada `sesion07` dentro del proyecto

```bash
mkdir sesion07
cd sesion07
```

Aquí guardaremos los ejemplos de la sesión

---

#### Dunder Methods

¿Qué son los Dunder Methods?

---
Los Dunder Methods, o "Double Underscore Methods", son métodos especiales en Python que permiten personalizar el comportamiento de las instancias de una clase. 

---
Son llamados también "métodos mágicos" o "métodos especiales".

Es el enfoque de Python para implementar el concepto de "sobrecarga"

Permitiendo a las clases definir un propio comportamiento con respecto a los operadores y funciones integradas del lenguaje.

---

#### Ventajas de los Dunder Methods

- **Personalización**: Permiten definir cómo se comportan las instancias de una clase en situaciones específicas, como la impresión, la comparación o la conversión a otros tipos.

- **Legibilidad**: Hacen que el código sea más intuitivo y fácil de entender.

---

- **Integración**: Crea compatibilidad con las funciones y operadores integrados de Python

- **Reutilización**: Reduce la cantidad de código necesario para implementar ciertas funcionalidades.


---

#### Usos Reales

- En las finanzas, para modelar valores monetarios y definir cómo se suman, restan o comparan.
- En la geometría, para modelar puntos, círculos facilitando su comportamiento entre sí.

---

En el mundo real varias librerías y frameworks utilizan Dunder Methods para definir el comportamiento de sus objetos.

- Pandas utiliza Dunder Methods para definir cómo se comportan los DataFrames al realizar operaciones matemáticas o lógicas.
- Django utiliza Dunder Methods para definir cómo se comportan los modelos al realizar consultas a la base de datos.

---

- SQLAlchemy utiliza Dunder Methods para definir cómo se comportan los objetos al realizar operaciones de base de datos.
- Request utiliza Dunder Methods para definir cómo se comportan las peticiones HTTP.

---

El uso de Dunder Methods es una práctica común en Python, y su comprensión es esencial para aprovechar al máximo el lenguaje.

Es parte de hacer que tu código sea más elegante, eficiente y fácil de mantener.

---

Se puede clasificar en:

- **Métodos de Inicialización y Destrucción**: `__init__`, `__del__`
- **Métodos de Representación y Conversión**: `__str__`, `__repr__`, `__int__`, `__float__`
- **Métodos de Comparación**: `__eq__`, `__lt__`, `__gt__`, `__le__`, `__ge__`, `__ne__`
- **Operadores Aritméticos**: `__add__`, `__sub__`, `__mul__`, `__truediv__`

---
#### Notación de Dunder Methods

Los Dunder Methods se definen con dos guiones bajos al principio y al final del nombre del método.

```python
def __init__(self, valor):
    self.valor = valor

def __str__(self):
    return f"Valor: {self.valor}"
```

---

#### Métodos de Inicialización y Destrucción

Permiten definir el comportamiento de una clase al ser creada o destruida.

Son utilizados para inicializar atributos o liberar recursos.

No retornan ningún valor.

Los más comunes son:

- `__init__` : Método de inicialización, se llama al crear una instancia de la clase.
- `__del__` : Método de destrucción, se llama al eliminar una instancia de la clase.

---
#### `__init__` - Método de Inicialización

El método `__init__` se utiliza para inicializar los atributos de una instancia de la clase.

Se utiliza al instanciar un objeto de la clase.

recibe como primer parámetro `self`, que es una referencia a la instancia de la clase.

Los siguientes parámetros son los atributos que se desean inicializar.

También se lo conoce como constructor de la clase.

```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
```

---

Su uso es fundamental para establecer el estado inicial de un objeto.

Se usa profesionalmente para definir los atributos de una clase y establecer su estado inicial.

---

#### `__del__` - Método de Destrucción

El método `__del__` se utiliza para liberar recursos o realizar acciones antes de que una instancia de la clase sea destruida.

Se llama automáticamente cuando el recolector de basura de Python elimina la instancia o cuando se utiliza la función `del` para eliminar una referencia a la instancia.

Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.

Su uso es menos común, ya que Python maneja automáticamente la memoria.

```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad

    def __del__(self):
        print(f"{self.nombre} ha sido destruido.")
```

---

Es útil para liberar recursos externos, como archivos abiertos o conexiones de red.

Se usa profesionalmente para realizar limpieza de recursos antes de que un objeto sea destruido.

---
#### Métodos de Representación y Conversión

Permiten definir cómo se representa una instancia de la clase como cadena de texto o cómo se convierte a otros tipos de datos.

Son utilizados para mejorar la legibilidad del código y facilitar la depuración.

Los más comunes son:

- `__repr__` : Método de representación oficial, se llama al utilizar la función `repr()`.
- `__str__` : Método de representación en cadena, se llama al utilizar la función `print()` o `str()`.

---

#### `__repr__` - Método de Representación Oficial

El método `__repr__` se utiliza para definir una representación oficial de la instancia de la clase.
Se utiliza al llamar a la función `repr()` o al imprimir la instancia en un entorno interactivo.
Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.
Debe retornar una cadena que represente el objeto de manera clara y precisa.
Con oficial se refiere a que debe ser una representación que pueda ser utilizada para recrear el objeto.
Se utiliza principalmente para depuración y desarrollo.
```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __repr__(self):
        return f"Persona(nombre='{self.nombre}', edad={self.edad})"
```

---
Su uso es fundamental para proporcionar una representación clara y precisa de un objeto.
Se usa profesionalmente para facilitar la depuración y el desarrollo, ya que permite ver el estado de un objeto de manera clara.

---

#### `__str__` - Método de Representación en Cadena
El método `__str__` se utiliza para definir una representación en cadena de la instancia de la clase.
Se utiliza al llamar a la función `print()` o `str()`.
Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.
Debe retornar una cadena que represente el objeto de manera legible.
Se utiliza principalmente para mostrar información al usuario o para imprimir el objeto.
```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __str__(self):
        return f"{self.nombre}, {self.edad} años"
```
---
Su uso es fundamental para proporcionar una representación legible de un objeto.
Se usa profesionalmente para mostrar información al usuario de manera clara y concisa.

---
#### Métodos de Conversión
Permiten definir cómo se convierte una instancia de la clase a otros tipos de datos.
Son utilizados para facilitar la conversión de objetos a tipos de datos nativos de Python.
Los más comunes son:
- `__int__` : Método de conversión a entero, se llama al utilizar la función `int()`.
- `__float__` : Método de conversión a flotante, se llama al utilizar la función `float()`.
- `__bool__` : Método de conversión a booleano, se llama al utilizar la función `bool()`.

---

#### `__int__` - Método de Conversión a Entero

El método `__int__` se utiliza para definir cómo se convierte una instancia de la clase a un entero.
Se utiliza al llamar a la función `int()`.
Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.
Debe retornar un valor entero que represente el objeto.
Se utiliza principalmente para convertir objetos a enteros.
```python
class Numero:
    def __init__(self, valor):
        self.valor = valor
    def __int__(self):
        return int(self.valor)
```
---
Su uso es fundamental para permitir la conversión de objetos a enteros.
Se usa profesionalmente para facilitar la conversión de objetos a tipos de datos nativos de Python

---
#### `__float__` - Método de Conversión a Flotante
El método `__float__` se utiliza para definir cómo se convierte una instancia de la clase a un flotante.
Se utiliza al llamar a la función `float()`.
Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.
Debe retornar un valor flotante que represente el objeto.
Se utiliza principalmente para convertir objetos a flotantes.
```python
class Numero:
    def __init__(self, valor):
        self.valor = valor
    def __float__(self):
        return float(self.valor)
```

---
Su uso es fundamental para permitir la conversión de objetos a flotantes.
Se usa profesionalmente para facilitar la conversión de objetos a tipos de datos nativos de Python

---
#### `__bool__` - Método de Conversión a Booleano
El método `__bool__` se utiliza para definir cómo se convierte una instancia de la clase a un valor booleano.
Se utiliza al llamar a la función `bool()` o para definir el comportamiento de un objeto en un contexto booleano, como una condición `if`.
Como el "truethiness" de un objeto.
Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.
Debe retornar `True` o `False` dependiendo del estado del objeto.
Se utiliza principalmente para determinar si un objeto es "verdadero" o "falso" en un contexto booleano.
```python
class Numero:
    def __init__(self, valor):
        self.valor = valor
    def __bool__(self):
        return self.valor != 0
```

---
Su uso es fundamental para permitir que los objetos se comporten correctamente en contextos booleanos.
Se usa profesionalmente para definir el comportamiento de un objeto en condicionales, como en sentencias `if` o bucles `while`.

---
#### Métodos de Comparación
Permiten definir cómo se comparan las instancias de la clase entre sí.
Son utilizados para facilitar la comparación de objetos en operaciones de ordenamiento, búsqueda y filtrado.
Los más comunes son:
- `__eq__` : Método de igualdad, se llama al utilizar el operador `==`.
- `__ne__` : Método de desigualdad, se llama al utilizar el operador `!=`.
- `__lt__` : Método de menor que, se llama al utilizar el operador `<`.
- `__le__` : Método de menor o igual que, se llama al utilizar el operador `<=`.
- `__gt__` : Método de mayor que, se llama al utilizar el operador `>`.
- `__ge__` : Método de mayor o igual que, se llama al utilizar el operador `>=`.

---
#### `__eq__` - Método de Igualdad
El método `__eq__` se utiliza para definir cómo se comparan dos instancias de la clase para determinar si son iguales.
Se utiliza al llamar al operador `==`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está comparando.
Debe retornar `True` si las instancias son iguales, o `False` en caso contrario.
Se utiliza principalmente para comparar objetos en operaciones de igualdad.
```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __eq__(self, otro):
        if isinstance(otro, Persona):
            return self.nombre == otro.nombre and self.edad == otro.edad
        return NotImplemented
```
#### `__ne__` - Método de Desigualdad
El método `__ne__` se utiliza para definir cómo se comparan dos instancias de la clase para determinar si son diferentes.
Se utiliza al llamar al operador `!=`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está comparando.
Debe retornar `True` si las instancias son diferentes, o `False` en caso contrario.
Se utiliza principalmente para comparar objetos en operaciones de desigualdad.
```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __ne__(self, otro):
        if isinstance(otro, Persona):
            return self.nombre != otro.nombre or self.edad != otro.edad
        return NotImplemented
```

---
##### `__lt__` - Método de Menor Que
El método `__lt__` se utiliza para definir cómo se comparan dos instancias de la clase para determinar si una es menor que la otra.
Se utiliza al llamar al operador `<`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está comparando.
Debe retornar `True` si la instancia `self` es menor que `otro`, o `False` en caso contrario.
Se utiliza principalmente para comparar objetos en operaciones de ordenamiento.
```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __lt__(self, otro):
        if isinstance(otro, Persona):
            return self.edad < otro.edad
        return NotImplemented
```
##### `__le__` - Método de Menor o Igual Que
El método `__le__` se utiliza para definir cómo se comparan dos instancias de la clase para determinar si una es menor o igual que la otra.
Se utiliza al llamar al operador `<=`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está comparando.
Debe retornar `True` si la instancia `self` es menor o igual que `otro`, o `False` en caso contrario.
Se utiliza principalmente para comparar objetos en operaciones de ordenamiento.
```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __le__(self, otro):
        if isinstance(otro, Persona):
            return self.edad <= otro.edad
        return NotImplemented
```
##### `__gt__` - Método de Mayor Que
El método `__gt__` se utiliza para definir cómo se comparan dos instancias de la clase para determinar si una es mayor que la otra.
Se utiliza al llamar al operador `>`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está comparando.
Debe retornar `True` si la instancia `self` es mayor que `otro`, o `False` en caso contrario.
Se utiliza principalmente para comparar objetos en operaciones de ordenamiento.
```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __gt__(self, otro):
        if isinstance(otro, Persona):
            return self.edad > otro.edad
        return NotImplemented
```
##### `__ge__` - Método de Mayor o Igual Que
El método `__ge__` se utiliza para definir cómo se comparan dos instancias de la clase para determinar si una es mayor o igual que la otra.
Se utiliza al llamar al operador `>=`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está comparando.
Debe retornar `True` si la instancia `self` es mayor o igual que `otro`, o `False` en caso contrario.
Se utiliza principalmente para comparar objetos en operaciones de ordenamiento.
```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __ge__(self, otro):
        if isinstance(otro, Persona):
            return self.edad >= otro.edad
        return NotImplemented
```

---

#### Operadores Aritméticos

Permiten definir cómo se comportan las instancias de la clase al utilizar operadores aritméticos.
Son utilizados para facilitar las operaciones matemáticas entre objetos.
Los más comunes son:
- `__add__` : Método de suma, se llama al utilizar el operador `+`.
- `__sub__` : Método de resta, se llama al utilizar el operador `-`.
- `__mul__` : Método de multiplicación, se llama al utilizar el operador `*`.
- `__truediv__` : Método de división, se llama al utilizar el operador `/`.
- `__floordiv__` : Método de división entera, se llama al utilizar el operador `//`.
- `__mod__` : Método de módulo, se llama al utilizar el operador `%`.
- `__pow__` : Método de potencia, se llama al utilizar el operador `**`.

---

#### `__add__` - Método de Suma

El método `__add__` se utiliza para definir cómo se suman dos instancias de la clase.
Se utiliza al llamar al operador `+`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está sumando.
Debe retornar una nueva instancia que represente el resultado de la suma.
Se utiliza principalmente para realizar operaciones de suma entre objetos.
```python
class Coordenada:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __add__(self, otro):
        if isinstance(otro, Coordenada):
            return Coordenada(self.x + otro.x, self.y + otro.y)
        return NotImplemented
```
---
#### `__sub__` - Método de Resta
El método `__sub__` se utiliza para definir cómo se restan dos instancias de la clase.
Se utiliza al llamar al operador `-`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está restando.
Debe retornar una nueva instancia que represente el resultado de la resta.
Se utiliza principalmente para realizar operaciones de resta entre objetos.
```python
class Coordenada:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __sub__(self, otro):
        if isinstance(otro, Coordenada):
            return Coordenada(self.x - otro.x, self.y - otro.y)
        return NotImplemented
```
---

#### `__mul__` - Método de Multiplicación
El método `__mul__` se utiliza para definir cómo se multiplican dos instancias de la clase.
Se utiliza al llamar al operador `*`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está multiplicando.
Debe retornar una nueva instancia que represente el resultado de la multiplicación.
Se utiliza principalmente para realizar operaciones de multiplicación entre objetos.
```python
class Coordenada:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __mul__(self, otro):
        if isinstance(otro, Coordenada):
            return Coordenada(self.x * otro.x, self.y * otro.y)
        return NotImplemented
```

---
#### `__truediv__` - Método de División
El método `__truediv__` se utiliza para definir cómo se dividen dos instancias de la clase.
Se utiliza al llamar al operador `/`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está dividiendo.
Debe retornar una nueva instancia que represente el resultado de la división.
Se utiliza principalmente para realizar operaciones de división entre objetos.
```python
class Coordenada:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __truediv__(self, otro):
        if isinstance(otro, Coordenada):
            return Coordenada(self.x / otro.x, self.y / otro.y)
        return NotImplemented
```

---
#### `__floordiv__` - Método de División Entera
El método `__floordiv__` se utiliza para definir cómo se realiza la división entera entre dos instancias de la clase.
Se utiliza al llamar al operador `//`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está realizando la división entera.
Debe retornar una nueva instancia que represente el resultado de la división entera.
Se utiliza principalmente para realizar operaciones de división entera entre objetos.
```python
class Coordenada:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __floordiv__(self, otro):
        if isinstance(otro, Coordenada):
            return Coordenada(self.x // otro.x, self.y // otro.y)
        return NotImplemented
```

---
#### `__mod__` - Método de Módulo
El método `__mod__` se utiliza para definir cómo se calcula el módulo entre dos instancias de la clase.
Se utiliza al llamar al operador `%`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está realizando el cálculo del módulo.
Debe retornar una nueva instancia que represente el resultado del módulo.
Se utiliza principalmente para realizar operaciones de módulo entre objetos.
```python
class Coordenada:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __mod__(self, otro):
        if isinstance(otro, Coordenada):
            return Coordenada(self.x % otro.x, self.y % otro.y)
        return NotImplemented
```

---
#### `__pow__` - Método de Potencia
El método `__pow__` se utiliza para definir cómo se calcula la potencia entre dos instancias de la clase.
Se utiliza al llamar al operador `**`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `otro`, que es la otra instancia con la que se está realizando el cálculo de la potencia.
Debe retornar una nueva instancia que represente el resultado de la potencia.
Se utiliza principalmente para realizar operaciones de potencia entre objetos.
```python
class Coordenada:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __pow__(self, otro):
        if isinstance(otro, Coordenada):
            return Coordenada(self.x ** otro.x, self.y ** otro.y)
        return NotImplemented
```

---

#### Otros Dunder Methods

Existen muchos otros Dunder Methods que permiten personalizar el comportamiento de las instancias de una clase en Python.
Algunos de los más comunes son:

- `__len__` : Método de longitud, se llama al utilizar la función `len()`.
- `__getitem__` : Método de obtención de elementos, se llama al utilizar el operador `[]`.
- `__setitem__` : Método de establecimiento de elementos, se llama al utilizar el operador `[]` para asignar un valor.
- `__delitem__` : Método de eliminación de elementos, se llama al utilizar el operador `del` con `[]`.
- `__iter__` : Método de iteración, se llama al utilizar la función `iter()`.
- `__next__` : Método de siguiente elemento, se llama al utilizar la función `next()`.
- `__contains__` : Método de pertenencia, se llama al utilizar el operador `in`.
- `__call__` : Método de llamada, se llama al utilizar la instancia como una función.
- `__hash__` : Método de hash, se llama al utilizar la función `hash()`.
- `__copy__` : Método de copia superficial, se llama al utilizar la función `copy.copy()`.
- `__deepcopy__` : Método de copia profunda, se llama al utilizar la función `copy.deepcopy()`.
- `__enter__` : Método de entrada, se llama al utilizar la declaración `with`.
- `__exit__` : Método de salida, se llama al utilizar la declaración `with`.

---
#### `__len__` - Método de Longitud
El método `__len__` se utiliza para definir cómo se calcula la longitud de una instancia de la clase.
Se utiliza al llamar a la función `len()`.
Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.
Debe retornar un valor entero que represente la longitud del objeto.
Se utiliza principalmente para obtener la longitud de objetos personalizados.
```python
class Librero:
    def __init__(self):
        self.libros = []
    def __len__(self):
        return len(self.libros)
```

---
Se utiliza especialmente en colecciones personalizadas, como listas o diccionarios, para definir su longitud.

---
#### `__getitem__` - Método de Obtención de Elementos
El método `__getitem__` se utiliza para definir cómo se obtienen los elementos de una instancia de la clase al utilizar notación de corchetes `[]`.
Se utiliza al llamar metodo `objeto[indice]`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `indice`, que es el índice del elemento que se desea obtener.
Debe retornar el elemento correspondiente al índice proporcionado.
Se utiliza principalmente para acceder a elementos de objetos personalizados como listas o diccionarios.
```python
class Librero:
    def __init__(self):
        self.libros = []
    def __getitem__(self, indice):
        return self.libros[indice]
```

---
#### `__setitem__` - Método de Establecimiento de Elementos

El método `__setitem__` se utiliza para definir cómo se establecen los elementos de una instancia de la clase al utilizar notación de corchetes `[]`.
Se utiliza al llamar metodo `objeto[indice] = valor`.
Recibe tres parámetros: `self`, que es una referencia a la instancia de la clase, `indice`, que es el índice del elemento que se desea establecer, y `valor`, que es el valor que se desea asignar al elemento.
Debe no retornar ningún valor.
Se utiliza principalmente para asignar valores a elementos de objetos personalizados como listas o diccionarios.
```python
class Librero:
    def __init__(self):
        self.libros = []
    def __setitem__(self, indice, valor):
        self.libros[indice] = valor
```

---
#### `__delitem__` - Método de Eliminación de Elementos
El método `__delitem__` se utiliza para definir cómo se eliminan los elementos de una instancia de la clase al utilizar notación de corchetes `[]`.
Se utiliza al llamar al operador `del` con `objeto[indice]`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `indice`, que es el índice del elemento que se desea eliminar.
No debe retornar ningún valor.
Se utiliza principalmente para eliminar elementos de objetos personalizados como listas o diccionarios.

```python
class Librero:
    def __init__(self):
        self.libros = []
    def __delitem__(self, indice):
        del self.libros[indice]
```

---

#### `__iter__` - Método de Iteración
El método `__iter__` se utiliza para definir cómo se itera sobre una instancia de la clase.
Se utiliza al llamar a la función `iter()`.
Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.
Debe retornar un iterador que permita recorrer los elementos de la instancia.
Se utiliza principalmente para permitir la iteración sobre objetos personalizados como listas o diccionarios.
```python
class Librero:
    def __init__(self):
        self.libros = []
    def __iter__(self):
        return iter(self.libros)
```

Es especialmente útil para permitir el uso de bucles `for` en objetos personalizados.

```python
librero = Librero()
librero.libros.append("Libro 1")
librero.libros.append("Libro 2")
for libro in librero:
    print(libro)
```

---

#### `__next__` - Método de Siguiente Elemento
El método `__next__` se utiliza para definir cómo se obtiene el siguiente elemento de una instancia de la clase durante la iteración.
Se utiliza al llamar a la función `next()`.
Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.
Debe retornar el siguiente elemento de la instancia o lanzar una excepción `StopIteration` si no hay más elementos.
Se utiliza principalmente para permitir la iteración sobre objetos personalizados.
```python
class Librero:
    def __init__(self):
        self.libros = []
        self.indice = 0
    def __iter__(self):
        self.indice = 0
        return self
    def __next__(self):
        if self.indice < len(self.libros):
            libro = self.libros[self.indice]
            self.indice += 1
            return libro
        else:
            raise StopIteration
```

#### `__contains__` - Método de Pertenencia
El método `__contains__` se utiliza para definir cómo se verifica si un elemento pertenece a una instancia de la clase.
Se utiliza al llamar al operador `in`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `elemento`, que es el elemento que se desea verificar si pertenece a la instancia.
Debe retornar `True` si el elemento pertenece a la instancia, o `False` en caso contrario.
Se utiliza principalmente para verificar la pertenencia de elementos en objetos personalizados como listas o diccionarios.
```python
class Librero:
    def __init__(self):
        self.libros = []
    def __contains__(self, elemento):
        return elemento in self.libros
# Uso
librero = Librero()
librero.libros.append("Libro 1")
print("Libro 1" in librero)  # True
```

---
#### `__call__` - Método de Llamada
El método `__call__` se utiliza para definir cómo se llama a una instancia de la clase como si fuera una función.
Se utiliza al llamar a la instancia de la clase con paréntesis `()`.
Recibe como primer parámetro `self`, que es una referencia a la instancia de la clase, y los siguientes parámetros son los argumentos que se pasan al llamar a la instancia.
Debe retornar un valor que represente el resultado de la llamada.
Se utiliza principalmente para permitir que las instancias de la clase se comporten como funciones.
```python
class Calculadora:
    def __call__(self, a, b):
        return a + b
class Suma(Calculadora):
    def __call__(self, a, b):
        return super().__call__(a, b)
# Uso
suma = Suma()
resultado = suma(3, 5)
print(resultado)  # 8
```

---

#### `__hash__` - Método de Hash
El método `__hash__` se utiliza para definir cómo se calcula el valor hash de una instancia de la clase.
Se utiliza al llamar a la función `hash()`.
Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.
Debe retornar un valor entero que represente el hash del objeto.
Se utiliza principalmente para permitir que las instancias de la clase se utilicen como claves en diccionarios o elementos en conjuntos.
```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __hash__(self):
        return hash((self.nombre, self.edad))
# Uso
persona1 = Persona("Alice", 30)
persona2 = Persona("Bob", 25)
print(hash(persona1))  # Hash de persona1
print(hash(persona2))  # Hash de persona2
```

---
#### `__copy__` - Método de Copia Superficial
El método `__copy__` se utiliza para definir cómo se realiza una copia superficial de una instancia de la clase.
Se utiliza al llamar a la función `copy.copy()`.
Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.
Debe retornar una nueva instancia que sea una copia superficial del objeto original.
Se utiliza principalmente para crear copias superficiales de objetos personalizados.
```python
import copy
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __copy__(self):
        return Persona(self.nombre, self.edad)
# Uso
persona1 = Persona("Alice", 30)
persona2 = copy.copy(persona1)
print(persona1.nombre)  # Alice
print(persona2.nombre)  # Alice
```

---
#### `__deepcopy__` - Método de Copia Profunda
El método `__deepcopy__` se utiliza para definir cómo se realiza una copia profunda de una instancia de la clase.
Se utiliza al llamar a la función `copy.deepcopy()`.
Recibe dos parámetros: `self`, que es una referencia a la instancia de la clase, y `memo`, que es un diccionario utilizado para rastrear objetos ya copiados.
Debe retornar una nueva instancia que sea una copia profunda del objeto original.
Se utiliza principalmente para crear copias profundas de objetos personalizados que contienen referencias a otros objetos.
```python
import copy
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    def __deepcopy__(self, memo):
        copia = Persona(self.nombre, self.edad)
        memo[id(self)] = copia
        return copia
# Uso
persona1 = Persona("Alice", 30)
persona2 = copy.deepcopy(persona1)
print(persona1.nombre)  # Alice
print(persona2.nombre)  # Alice
```

---

#### `__enter__` - Método de Entrada
El método `__enter__` se utiliza para definir el comportamiento al entrar en un contexto de administración de recursos, como al utilizar la declaración `with`.
Se utiliza al iniciar un bloque `with`.
Recibe como único parámetro `self`, que es una referencia a la instancia de la clase.
Debe retornar el objeto que se utilizará dentro del bloque `with`.
Se utiliza principalmente para inicializar recursos o realizar configuraciones antes de ejecutar el bloque `with`.

---

#### `__exit__` - Método de Salida
El método `__exit__` se utiliza para definir el comportamiento al salir de un contexto de administración de recursos, como al utilizar la declaración `with`.
Se utiliza al finalizar un bloque `with`.
Recibe cuatro parámetros: `self`, que es una referencia a la instancia de la clase, `exc_type`, `exc_value` y `traceback`, que son utilizados para manejar excepciones que puedan ocurrir dentro del bloque `with`.
No debe retornar ningún valor.
Se utiliza principalmente para liberar recursos o realizar limpieza después de ejecutar el bloque `with`.
```python
class AdministradorRecursos:
    def __enter__(self):
        print("Entrando en el contexto")
        return self
    def __exit__(self, exc_type, exc_value, traceback):
        print("Saliendo del contexto")
# Uso
with AdministradorRecursos() as admin:
    print("Dentro del bloque with")
```

---





---
<!-- .slide: data-background-image="../../content/psg-bg-dark.png" data-background-size="100%"-->

<br>
<br>
<br>
<br>
<br>

[![GitHub](../../content/github_logo.png) <!-- .element width="20%"-->](https://github.com/python-la-paz/python-study-group-oop/content/sesion08)

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
https://www.pythonmorsels.com/every-dunder-method/
https://docs.python.org/3/library/operator.html
https://docs.python.org/3/reference/datamodel.html#object.__len__
https://www.pythonmorsels.com/terms/#dunder
https://docs.python.org/3/reference/datamodel.html#special-method-names
https://diveintopython.org/es/learn/classes/dunder-magic-methods
https://web.archive.org/web/20110131211638/http://diveintopython3.org/special-method-names.html
