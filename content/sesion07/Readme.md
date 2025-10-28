<!-- .slide: data-background-image="../../content/psg-bg-dark.png" data-background-size="100%"-->
![Python La paz](../Logo.png) <!-- .element  hidden="true" -->

<br>
<br>
<br>

### Sesión  07
#### Polimorfismo
#### Flexibilidad en el diseño de objetos

---
### Antes de empezar

---

#### Proyecto en VSCode

Abre el proyecto en VSCode

```bash
code psg-oop-2025
```

Crea una carpeta con el nombre `sesion07`

```bash
mkdir sesion07
cd sesion07
```

- Los archivos de esta sesión deben estar dentro de esta carpeta

- Al finalizar la sesión, sube los cambios al repositorio en un commit

---

#### **Duck Typing**

En programación orientada a objetos es una **técnica** que desempeña un papel importante en la **flexibilidad** y **reutilización** del código

Bajo la premisa

---

> Si camina como un pato, suena como un pato y nada como un pato
> entonces probablemente sea

### **un pato 🦆**  <!-- .element class="fragment" data-fragment-index="2"-->

---

¿Qué significa esto?

Significa que **NO** importa el tipo de un objeto, sino como se comporta

---

Python destaca por su enfoque de tipado **dinámico** y **flexibilidad** para trabajar con diferentes tipos de datos

---

En lugar de enfocarse en el **tipo** específico de un objeto, Python se enfoca en el **comportamiento** del objeto

> Si un objeto *puede* realizar las operaciones requeridas, Python lo acepta como *válido*

---
Un ejemplo de duck typing en Python es la función `len()`

Cuando llamamos a `len()` no importa el tipo de dato que le pasamos

---

| Tipo de dato         | Ejemplo            | ¿Qué hace `len()`?    | Res |
| -------------------- | ------------------ | --------------------- | --- |
| `str` (cadena)       | `"hola"`           | Cuenta **caracteres** | `4` |
| `list` (lista)       | `[1, 2, 3]`        | Cuenta **elementos**  | `3` |
| `tuple` (tupla)      | `(1, 2)`           | Cuenta **elementos**  | `2` |
| `dict` (diccionario) | `{"a": 1, "b": 2}` | Cuenta **claves**     | `2` |

---

#### Ventajas del Duck Typing

**Flexibilidad**: Permite que diferentes tipos de objetos sean utilizados de manera intercambiable si cumplen con el comportamiento esperado

**Reutilización de código**: Facilita la creación de funciones dinámicas

---

#### Desventajas del Duck Typing

**Errores en tiempo de ejecución**: Si un objeto no cumple con el comportamiento esperado, puede generar errores en tiempo de ejecución

**Dificultad para depurar**: Puede ser más difícil rastrear errores relacionados con el tipo de objeto

---

#### Ejemplo 01

Crear el archivo `discman.md`  y el archivo `discman.py` en la carpeta `sesion07`

```markdown
La empresa `PySound` desarrolla un Discman para niños
reproduce sonidos de animales y muestra el nombre del animal en
su pantalla. Actualmente tiene los siguientes animales:
- Pato 🦆 (Cuac, Cuac)
- Gato 🐱 (Miau, Miau)
```

---

Análisis

```markdown
# Analisis
Requisitos
- El Discman debe reproducir sonidos de animales
- Debe mostrar el animal que emite el sonido
- El pato debe emitir el sonido "cuac"
- El gato debe emitir el sonido "miau"
- Debe reproducir el sonido del pato
- Debe reproducir el sonido del gato

Objetos
- Pato
- Gato
- Discman

Características
- Pato:
    - sonido "cuac"
- Gato:
    - sonido "miau"

Acciones
- Pato: emitir sonido
- Gato: emitir sonido
- Discman: reproducir sonido
```

---

Diseño diagrama en Mermaid

````
```mermaid
classDiagram
    class Pato {
        sonido: String
        +emitir_sonido()
    }
    
    class Gato {
        sonido: String
        +emitir_sonido()
    }

    class Discman {
        +reproducir_sonido(animal)
    }
```	
````

---

Diseño Diagrama

```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
    class Pato {
        sonido: String
        +emitir_sonido()
    }
    
    class Gato {
        sonido: String
        +emitir_sonido()
    }

    class Discman {
        +reproducir_sonido(animal)
    }
```
<!--.element class="center-mermaid"-->

---

Tanto el `Pato` como el `Gato` tienen el mismo método

`emitir_sonido()`

`Discman` utilizará ese nombre de método para reproducir el sonido de cualquier animal

---

En el archivo `discman.py` 

```python [1-14|15-20]
# Definición
class Pato:
    sonido = "cuac"
    def emitir_sonido(self):
        print (f"El pato 🦆 hace: {self.sonido}")

class Gato:
    sonido = "miau"
    def emitir_sonido(self):
        print (f"El gato 🐱 hace: {self.sonido}")

class Discman:
    def reproducir_sonido(self, objeto):
        objeto.emitir_sonido()
# Uso
pato = Pato()
gato = Gato()
discman = Discman()
discman.reproducir_sonido(pato)
discman.reproducir_sonido(gato)
```

```text
El pato 🦆 hace: cuac
El gato 🐱 hace: miau
```

---

#### Ejercicio para ti (02)

En la carpeta **sesion05** modifica los archivos **discman.md** y **discman.py**

```markdown
La empresa `PySound` quiere mejorar su Discman para niños.
Le añaden la capacidad de reproducir sonidos
de objetos que no son animales,
añadiendo los siguientes instrumentos:
- Campana que hace "ding"
- Tambor que hace "boom"
```

Obtener el *Análisis*

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

---

Modificando el *Análisis*

```markdown [10-13|18,19,26-29,35-36]
# Analisis

Requisitos
- El Discman debe reproducir sonidos de animales
- Debe mostrar el animal que emite el sonido
- El pato debe emitir el sonido "cuac"
- El gato debe emitir el sonido "miau"
- Debe reproducir el sonido del pato
- Debe reproducir el sonido del gato
- La campana debe emitir el sonido "ding"
- El tambor debe emitir el sonido "boom"
- Debe reproducir el sonido de la campana
- Debe reproducir el sonido del tambor
Objetos
- Pato
- Gato
- Discman
- Campana
- Tambor

Características
- Pato:
    - sonido "cuac"
- Gato:
    - sonido "miau"
- Campana:
    - sonido "ding"
- Tambor:
    - sonido "boom"

Acciones
- Pato: emitir sonido
- Gato: emitir sonido
- Discman: reproducir sonido
- Campana: emitir sonido
- Tambor: emitir sonido
```

---

#### Ejercicio para ti (02)

Ahora obtenemos el diseño del *diagrama de clase*

2 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Modifica el archivo `discman.md`

---

Modificando el diseño de diagrama de clases

```` [13-21]
```mermaid
classDiagram
    class Pato {
        sonido: String
        +emitir_sonido()
    }
    
    class Gato {
        sonido: String
        +emitir_sonido()
    }

    class Campana {
        sonido: String
        +emitir_sonido()
    }

    class Tambor {
        sonido: String
        +emitir_sonido()
    }

    class Discman {
        +reproducir_sonido(objeto)
    }
```	
````

---

Modificando el diseño de diagrama de clases

```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
    class Pato {
        sonido: String
        +emitir_sonido()
    }
    
    class Gato {
        sonido: String
        +emitir_sonido()
    }

    class Campana {
        sonido: String
        +emitir_sonido()
    }

    class Tambor {
        sonido: String
        +emitir_sonido()
    }

    class Discman {
        +reproducir_sonido(objeto)
    }
```
<!--.element class="center-mermaid"-->

---

#### Ejercicio para ti (02)

Ya tenemos el *análisis y diseño* de la clase

Ahora podemos **programar**

Modifica el archivo `discman.py`

3 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

---

Implementando las clases

```python [12-20|31-34]
# Definición
class Pato:
    sonido = "cuac"
    def emitir_sonido(self):
        print (f"El pato 🦆 hace: {self.sonido}")

class Gato:
    sonido = "miau"
    def emitir_sonido(self):
        print (f"El gato 🐱 hace: {self.sonido}")

class Campana:
    sonido = "ding"
    def emitir_sonido(self):
        print (f"La campana 🔔 hace: {self.sonido}")

class Tambor:
    sonido = "boom"
    def emitir_sonido(self):
        print (f"El tambor 🥁 hace: {self.sonido}")

class Discman:
    def reproducir_sonido(self, objeto):
        objeto.emitir_sonido()
# Uso
pato = Pato()
gato = Gato()
discman = Discman()
discman.reproducir_sonido(pato)
discman.reproducir_sonido(gato)
campana = Campana()
tambor = Tambor()
discman.reproducir_sonido(campana)
discman.reproducir_sonido(tambor)
```

---

Ejecución del código

```bash
python discman.py
```

```text
El pato 🦆 hace: cuac
El gato 🐱 hace: miau
La campana 🔔 hace: ding
El tambor 🥁 hace: boom
```

---

El Duck Typing permite que la `Discman` trabaje con diferentes tipos de objetos
siempre y cuando tengan el método `emitir_sonido()`

Esto hace que el código sea más flexible y reutilizable

---

#### Polimorfismo

¿Qué es el polimorfismo?

---

Viene del griego

**poly** = "muchos"

**morphē** = "formas"

*→* **polymorphos** = "muchas formas"

![Polimorfismo](./img/polimorph.gif) <!-- .element  width="30%"-->

---

#### Principios fundamentales

Es el **4º** y **último** principio fundamental de la Programación Orientada a Objetos (POO)

## **Polimorfismo**

## **o** 

## **Sobrecarga** 

---

Es la capacidad de usar un mismo método para trabajar con diferentes tipos de objetos.

Esto permite que diferentes clases implementen el mismo método de manera diferente

---

Por ejemplo, en nuestro caso, tanto el `Pato`, el `Gato`, la `Campana` y el `Tambor` tienen un método `emitir_sonido()`

Pero cada uno de ellos emite un sonido diferente

---

El polimorfismo permite que la `Discman` llame al método `emitir_sonido()` de cualquier objeto que se le pase, sin importar su tipo específico

---
Esto es posible gracias al duck typing, 

ya que la `Discman` no necesita conocer el tipo exacto de objeto que recibe,

solo necesita que el objeto tenga un método `emitir_sonido()`

---

Podemos ver polimorfismo mediante:

- Herencia
- Sobrecarga de métodos
- Sobrecarga de operadores

---

#### Polimorfismo con herencia

Una clase base define un método y las clases hijas lo implementan de manera específica

---

El polimorfismo con herencia permite que una clase base defina un método general
y las clases hijas lo implementen de manera única de acuerdo a sus necesidades

---

#### Ejemplo 03

Crear el archivo `herencia.md` y el archivo `herencia.py` en la carpeta `sesion07`


```markdown
Una empresa de delívery `PyHL` tiene diferentes
tipos de vehículos para transportar paquetes,
sus vehículos más comunes son:

🚗 Auto: terrestre, a gasolina
🚲 Bicicleta: terrestre, a pedal

Los vehículos pueden moverse para transportar paquetes
```

---

En el archivo `herencia.md` 

```markdown
# Análisis
Requisitos
- Los autos pueden moverse mediante motor a gasolina
- Las bicicletas pueden moverse mediante pedales

Objetos
- Vehículo
    - Auto
    - Bicicleta

Características
- Vehículo: tipo, energia
- Auto: tipo, energia
- Bicicleta: tipo, energia

Acciones
- Vehículo: moverse
- Auto: moverse
- Bicicleta: moverse
```

Ahora que tenemos los requisitos, características y acciones, podemos definir el diseño

---

#### Diagrama de clases

````
```mermaid
classDiagram
    class Vehiculo {
        + tipo
        + energia
        + moverse()
    }
    class Auto {
        + moverse()
    }
    class Bicicleta {
        + moverse()
    }
    Vehiculo <|-- Auto
    Vehiculo <|-- Bicicleta
```
````

---

#### Diagrama de clases

```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
    class Vehiculo {
        + tipo
        + energia
        + moverse()
    }
    class Auto {
        + moverse()
    }
    class Bicicleta {
        + moverse()
    }
    Vehiculo <|-- Auto
    Vehiculo <|-- Bicicleta
```

---

#### Implementación en Python

En el archivo `herencia.py` 

```python
# Definición
class Vehiculo:
    def __init__(self, tipo, energia):
        self.tipo = tipo
        self.energia = energia
    
    def moverse(self):
        print(f"El vehículo {self.tipo}")
        print(f"Se mueve con {self.energia}")

class Auto(Vehiculo):
    def __init__(self):
        super().__init__("Terrestre", "motor a gasolina")
    
    def moverse(self):
        print("El 🚗 avanza a 200 km/h")
        print(f"Utiliza {self.energia} y es {self.tipo}")

class Bicicleta(Vehiculo):
    def __init__(self):
        super().__init__("Terrestre", "pedales")
    
    def moverse(self):
        print("La 🚲 avanza a 20 km/h")
        print(f"Es {self.tipo} y {self.energia}")
# Uso
auto = Auto()
bicicleta = Bicicleta()
auto.moverse()
bicicleta.moverse()
```

```text
El 🚗 avanza a 200 km/h
Utiliza motor a gasolina y es Terrestre
La 🚲 avanza a 20 km/h
Es Terrestre y pedales
```

---

#### Ejemplo 04

Añadir dos nuevos vehículos a la empresa `PyHL`:

```markdown
- ✈️ Avión: aéreo, a gasolina
- ⛵ Bote: acuático, a viento
```

Hacer el análisis 1 minuto

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Añadir al archivo `herencia.md`

---

Análisis

```markdown [5-6|12-13|19-20|26-27]
# Análisis
Requisitos
- Los autos pueden moverse mediante motor a gasolina
- Las bicicletas pueden moverse mediante pedales
- Los aviones pueden moverse mediante motor a gasolina
- Los botes pueden moverse mediante viento

Objetos
- Vehículo
    - Auto
    - Bicicleta
    - Avión
    - Bote

Características
- Vehículo: tipo, energia
- Auto: tipo, energia
- Bicicleta: tipo, energia
- Avión: tipo, energia
- Bote: tipo, energia

Acciones
- Vehículo: moverse
- Auto: moverse
- Bicicleta: moverse
- Avión: moverse
- Bote: moverse
```

---

Ahora que tenemos los requisitos, características y acciones podemos definir el diseño

2 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Añadir al archivo `herencia.md`

---

#### Diagrama de clases

```` [14-19|22-23]
```mermaid
classDiagram
    class Vehiculo {
        + tipo
        + energia
        + moverse()
    }
    class Auto {
        + moverse()
    }
    class Bicicleta {
        + moverse()
    }
    class Avion {
        + moverse()
    }
    class Bote {
        + moverse()
    }
    Vehiculo <|-- Auto
    Vehiculo <|-- Bicicleta
    Vehiculo <|-- Avion
    Vehiculo <|-- Bote
```
````

---

#### Diagrama de clases

```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
    class Vehiculo {
        + tipo
        + energia
        + moverse()
    }
    class Auto {
        + moverse()
    }
    class Bicicleta {
        + moverse()
    }
    class Avion {
        + moverse()
    }
    class Bote {
        + moverse()
    }
    Vehiculo <|-- Auto
    Vehiculo <|-- Bicicleta
    Vehiculo <|-- Avion
    Vehiculo <|-- Bote
```

---

Ya tenemos el análisis y el diagrama de clases, ahora podemos implementar el código

3 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Añadir al archivo `herencia.py`

---

```python [27-41|47-50]
# Definición
class Vehiculo:
    def __init__(self, tipo, energia):
        self.tipo = tipo
        self.energia = energia
    
    def moverse(self):
        print(f"El vehículo {self.tipo}")
        print(f"Se mueve con {self.energia}")

class Auto(Vehiculo):
    def __init__(self):
        super().__init__("Terrestre", "motor a gasolina")
    
    def moverse(self):
        print("El 🚗 avanza a 200 km/h")
        print(f"Utiliza {self.energia} y es {self.tipo}")

class Bicicleta(Vehiculo):
    def __init__(self):
        super().__init__("Terrestre", "pedales")
    
    def moverse(self):
        print("La 🚲 avanza a 20 km/h")
        print(f"Es {self.tipo} y {self.energia}")

class Avion(Vehiculo):
    def __init__(self):
        super().__init__("Aéreo", "motor a gasolina")
    
    def moverse(self):
        print("El ✈️ vuela a 900 km/h")
        print(f"Utiliza {self.energia} y es {self.tipo}")

class Bote(Vehiculo):
    def __init__(self):
        super().__init__("Acuático", "viento")
    
    def moverse(self):
        print("El ⛵ navega a 30 km/h")
        print(f"Utiliza {self.energia} y es {self.tipo}")
# Uso
auto = Auto()
bicicleta = Bicicleta()
auto.moverse()
bicicleta.moverse()
avion = Avion()
bote = Bote()
avion.moverse()
bote.moverse()
```

```text
El 🚗 avanza a 200 km/h
Utiliza motor a gasolina y es Terrestre
La 🚲 avanza a 20 km/h
Es Terrestre y pedales
El ✈️ vuela a 900 km/h
Utiliza motor a gasolina y es Aéreo
El ⛵ navega a 30 km/h
Utiliza viento y es Acuático
```

---

#### Sobrecarga de métodos

Consiste en definir múltiples métodos con el mismo nombre dentro de una clase, pero con diferentes implementaciones

```text
clase Persona 
    método hablar() 
        // Emite un sonido genérico

    método hablar(frase)
        // Habla con una frase
```

---

En otros lenguajes puede existir en la misma clase un método con el mismo nombre pero con diferentes parámetros

---
En Python, esto NO es posible

Python no permite la sobrecarga de métodos por parámetros

Pero, se puede lograr un comportamiento similar utilizando argumentos por defecto o argumentos variables `*args` y `**kwargs`

---

#### Ejemplo 05

Crear el archivo `metodos.md` y el archivo `metodos_01.py` en la carpeta `sesion07`

```markdown
Una empresa de mensajería `PyMS` tiene diferentes tipos
de mensajes que pueden enviar:
- Mensajes de texto
- Mensajes de audio
De acuerdo al tipo de mensaje, se debe enviar de manera diferente
```

---

En el archivo `metodos.md` 

```markdown
# Análisis
Requisitos
- Los mensajes de texto deben enviarse como texto
- Los mensajes de audio deben enviarse como sonido
Objetos
- Mensaje

Características
- Mensaje: contenido

Acciones
- Mensaje: enviar()
```

Ahora que tenemos los requisitos, características y acciones, podemos definir el diseño

---

#### Diagrama de clases

````
```mermaid
classDiagram
    class Mensaje {
        + contenido
        + enviar(tipo)
    }
```
````

```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
    class Mensaje {
        + contenido
        + enviar(tipo)
    }
```

---
#### Implementación en Python I

En `metodos_01.py` usando parámetros por defecto

```python
# Definición
class Mensaje:
    def __init__(self, contenido):
        self.contenido = contenido
    def enviar(self, audio=False):
        if audio:
            print(f"📣 {self.contenido}")
        else:
            print(f"💬 {self.contenido}")
# Uso
mensaje = Mensaje("Hola, ¿cómo estás?")
mensaje.enviar()
mensaje.enviar(audio=True)
```

```text
💬 Hola, ¿cómo estás?
📣 Hola, ¿cómo estás?
```

---
#### Implementacion en Python II

En `métodos_02.py` usando argumentos variables

```python
# Definición
class Mensaje:
    def __init__(self, contenido):
        self.contenido = contenido
    def enviar(self, *args):
        if "audio" in args:
            print(f"📣 {self.contenido}")
        if "texto" in args:
            print(f"💬 {self.contenido}")
# Uso
mensaje = Mensaje("Hola, ¿cómo estás?")
mensaje.enviar("texto")
mensaje.enviar("audio")
mensaje.enviar("video")
```

```text
💬 Hola, ¿cómo estás?
📣 Hola, ¿cómo estás?
```

---
#### Ejemplo 06

Añadir un nuevo tipo de mensaje a la empresa `PyMS`:

```markdown
- Mensajes mediante video
```

Hacer el análisis 1 minuto

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Añadir al archivo `metodos.md`

---

```markdown [5]
# Análisis
Requisitos
- Los mensajes de texto deben enviarse como texto
- Los mensajes de audio deben enviarse como sonido
- Los mensajes de video deben enviarse como video
Objetos
- Mensaje

Características
- Mensaje: contenido

Acciones
- Mensaje: enviar()
```

---

Ahora que tenemos los requisitos, características y acciones, podemos definir el diseño

En este caso, no cambiaremos el diagrama de clases, ya que el mensaje sigue siendo el mismo objeto

---

#### Diagrama de clases

````
```mermaid
classDiagram
    class Mensaje {
        + contenido
        + enviar(tipo)
    }
```
````
```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
    class Mensaje {
        + contenido
        + enviar(tipo)
    }
```

---

Ya tenemos el análisis y el diagrama de clases, ahora podemos implementar el código

3 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Añadir al archivo `metodos_01.py` y `metodos_02.py`

---

En  `metodos_01.py` usando parametros por defecto

```python [5-11|13-17]
# Definición
class Mensaje:
    def __init__(self, contenido):
        self.contenido = contenido
    def enviar(self, audio=False, video=False):
        if audio:
            print(f"📣 {self.contenido}")
        if video:
            print(f"🎥 {self.contenido}")
        if not audio and not video:
            print(f"💬 {self.contenido}")
# Uso
mensaje = Mensaje("Hola, ¿cómo estás?")
mensaje.enviar()
mensaje.enviar(audio=True)
mensaje.enviar(video=True)
mensaje.enviar(audio=True, video=True)
```

```text
💬 Hola, ¿cómo estás?
📣 Hola, ¿cómo estás?
🎥 Hola, ¿cómo estás?
📣 Hola, ¿cómo estás?
🎥 Hola, ¿cómo estás?
```

---

En  `métodos_02.py` usando argumentos variables

```python [5-11|13-17]
# Definición
class Mensaje:
    def __init__(self, contenido):
        self.contenido = contenido
    def enviar(self, *args):
        if "audio" in args:
            print(f"📣 {self.contenido}")
        if "texto" in args:
            print(f"💬 {self.contenido}")
        if "video" in args:
            print(f"🎥 {self.contenido}")
# Uso
mensaje = Mensaje("Hola, ¿cómo estás?")
mensaje.enviar("texto")
mensaje.enviar("audio")
mensaje.enviar("video")
mensaje.enviar("audio", "video")
```

```text
💬 Hola, ¿cómo estás?
📣 Hola, ¿cómo estás?
🎥 Hola, ¿cómo estás?
📣 Hola, ¿cómo estás?
🎥 Hola, ¿cómo estás?
```

---

#### Sobrecarga de operadores

La sobrecarga de operadores es la capacidad de definir el comportamiento de los operadores para objetos personalizados

Los operadores como `+`, `-`, `*`, `/`, pueden ser redefinidos para trabajar con instancias de clases

---
Por ejemplo, en Python con el operador `+` podemos sumar números y también concatenar cadenas

```python
a = 5
b = 10
c = a + b  # Suma de números
d = "Hola"
e = "Mundo"
f = d + " " + e  # Concatenación de cadenas
```

---
En Python se pueden definir métodos especiales para sobrecargar operadores

Estos métodos tienen nombres específicos que comienzan y terminan con dos guiones bajos `__`

---

| Operador | Método especial |
| -------- | --------------- |
| `+`      | `__add__`       |
| `-`      | `__sub__`       |
| `*`      | `__mul__`       |
| `/`      | `__truediv__`   |
| `//`     | `__floordiv__`  |
| `%`      | `__mod__`       |
| `**`     | `__pow__`       |

---

Es una buena práctica definir métodos generales privados o protegidos

para que se puedan reutilizar en los métodos especiales de los operadores

---

#### Ejemplo 07

Crear el archivo `operadores.md` y el archivo `operadores.py` en la carpeta `sesion07`

```markdown
Una profesor de matemáticas quiere crear una calculadora
de vectores bidimensionales, los vectores tienen
dos componentes: x e y. Los vectores pueden sumarse y restarse
entre sí utilizando los operadores `+` y `-`
Se pueden mostrar los vectores como `(x, y)`
```

En el archivo `operadores.md` 

---

#### Análisis

```markdown
# Análisis
Requisitos
- Los vectores deben tener componentes x e y
- Los vectores pueden sumarse y restarse entre sí
- Los vectores se pueden mostrar como `(x, y)`
Objetos
- Vector
Características
- Vector: x, y
Acciones
- Vector: sumar, restar, mostrar
```

---

#### Diagrama de clases

````
```mermaid
classDiagram
    class Vector {
        + x
        + y
        - sumar(vector)
        - restar(vector)
        + mostrar()
    }
```
````

```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
    class Vector {
        + x
        + y
        - sumar(vector)
        - restar(vector)
        + mostrar()
    }
```

---
#### Implementación en Python
En el archivo `operadores.py` 

```python
# Definición
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __sumar(self, vector):
        return Vector(self.x + vector.x, self.y + vector.y)
    def __restar(self, vector):
        return Vector(self.x - vector.x, self.y - vector.y)
    def mostrar(self):
        return f"({self.x}, {self.y})"
    def __add__(self, vector):
        return self.__sumar(vector)
    def __sub__(self, vector):
        return self.__restar(vector)
# Uso
vector1 = Vector(1, 1)
vector2 = Vector(2, 3)
vector3 = vector1 + vector2  # Suma de vectores
vector4 = vector1 - vector2  # Resta de vectores
print(f"A: {vector1.mostrar()}")
print(f"B: {vector2.mostrar()}")
print(f"A+B: {vector3.mostrar()}")
print(f"A-B: {vector4.mostrar()}")
```

```text
A: (1, 1)
B: (2, 3)
A+B: (3, 4)
A-B: (-1, -2)
```

---

#### Ejemplo 08

Añadir nuevas características a la calculadora de vectores:

```markdown
- Los vectores pueden multiplicarse y dividise
utilizando el operador `*` y `/`
- Los vectores pueden multiplicarse por un escalar
- Los vectores pueden dividirse por un escalar
Ejemplo:
- `(2, 4) * 2 = (4, 8)`
- `(2, 4) / 2 = (1, 2)`
```

Hacer el análisis 1 minuto

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

---

```markdown [6-9|16]
# Análisis
Requisitos
- Los vectores deben tener componentes x e y
- Los vectores pueden sumarse y restarse entre sí
- Los vectores se pueden mostrar como `(x, y)`
- Los vectores pueden multiplicarse por el operador `*`
- Los vectores pueden dividirse por el operador `/`
- Los vectores pueden multiplicarse por un escalar
- Los vectores pueden dividirse por un escalar
Objetos
- Vector
Características
- Vector: x, y
Acciones
- Vector: sumar, restar, mostrar
- Vector: multiplicar, dividir
```

---

Ahora que tenemos los requisitos, características y acciones, podemos definir el diseño

2 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Añadir al archivo `operadores.md`

---

```` [9-10]
```mermaid
classDiagram
    class Vector {
        + x
        + y
        - sumar(vector)
        - restar(vector)
        + mostrar()
        - multiplicar(escalar)
        - dividir(escalar)
    }
```
````

```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
    class Vector {
        + x
        + y
        - sumar(vector)
        - restar(vector)
        + mostrar()
        - multiplicar(escalar)
        - dividir(escalar)
    }
```

---

Ya tenemos el análisis y el diagrama de clases, ahora podemos implementar el código

3 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Añadir al archivo `operadores.py`

---

```python [10-16|23-26|36-39]
# Definición
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __sumar(self, vector):
        return Vector(self.x + vector.x, self.y + vector.y)
    def __restar(self, vector):
        return Vector(self.x - vector.x, self.y - vector.y)
    def __multiplicar(self, escalar):
        return Vector(self.x * escalar, self.y * escalar)
    def __dividir(self, escalar):
        if escalar != 0:
            return Vector(self.x / escalar, self.y / escalar)
        else:
            raise ValueError("No se puede dividir por cero")
    def mostrar(self):
        return f"({self.x}, {self.y})"
    def __add__(self, vector):
        return self.__sumar(vector)
    def __sub__(self, vector):
        return self.__restar(vector)
    def __mul__(self, escalar):
        return self.__multiplicar(escalar)
    def __truediv__(self, escalar):
        return self.__dividir(escalar)
# Uso
vector1 = Vector(1, 1)
vector2 = Vector(2, 3)
vector3 = vector1 + vector2  # Suma de vectores
vector4 = vector1 - vector2  # Resta de vectores
print(f"A: {vector1.mostrar()}")
print(f"B: {vector2.mostrar()}")
print(f"A+B: {vector3.mostrar()}")
print(f"A-B: {vector4.mostrar()}")
vector5 = vector1 * 2  # Multiplicación por escalar
vector6 = vector2 / 2  # División por escalar
print(f"A*2: {vector5.mostrar()}")
print(f"B/2: {vector6.mostrar()}")
```

```text
A: (1, 1)
B: (2, 3)
A+B: (3, 4)
A-B: (-1, -2)
A*2: (2, 2)
B/2: (1.0, 1.5)
```

---

#### Resumen

- El duck typing en Python permite que los objetos sean utilizados según su comportamiento y no por su tipo específico.
- El duck typing otorga flexibilidad y reutilización de código, pero puede causar errores en tiempo de ejecución si un objeto no cumple con el comportamiento esperado.

---

- El polimorfismo es la capacidad de usar un mismo método para trabajar con diferentes tipos de objetos, permitiendo que cada clase implemente el método de manera diferente.
- El polimorfismo se puede lograr mediante herencia, sobrecarga de métodos y sobrecarga de operadores.

---

- La herencia permite que una clase base defina métodos generales y que las clases hijas los implementen de manera específica.
- En Python la sobrecarga de métodos por parámetros no es posible, pero se puede simular usando argumentos por defecto `*args` y `**kwargs`.

---

- La sobrecarga de operadores permite definir el comportamiento de los operadores como +, -, *, / para objetos personalizados mediante métodos especiales.
- Es buena práctica definir métodos generales privados o protegidos para reutilizarlos en la sobrecarga de operadores.

---

#### Retos

Crear una carpeta con el nombre "retos_sesion_07" dentro del proyecto en la raíz, en la cual por cada ejercicio debes crear los siguientes archivos:

```bash
# Estructura de carpetas
psg-oop-2025/
    retos_sesion_07/
        ejercicio_01.md
        ejercicio_01.py
        ejercicio_02.md
        ejercicio_02.py
        ejercicio_03.md
        ejercicio_03.py
```

---

1. Un taller de carpintería guarda diferentes herramientas (por ejemplo, martillo, destornillador, llave inglesa).
Cada herramienta se puede "usar". La persona que usa la herramienta con la acción "utilizar" debe poder usar cualquier herramienta sin importar su tipo.

   - Crea un análisis, diagrama de clases y código que implemente el duck typing.
   - Debes crear al menos 2 herramientas diferentes.

---

2. Imagina que estás diseñando una aplicación para aprender a tocar instrumentos musicales.
hay varios instrumentos disponibles para el usuario. 
Aunque todos son instrumentos y se pueden "tocar", cada uno tiene una forma diferente de sonar:
```
la guitarra hace "strum"
el piano hace "plin"
el tambor hace "boom"
```

    - Crea un análisis, diagrama de clases y código que implemente polimorfismo con herencia.
    - Debes crear al menos 2 instrumentos diferentes.


---

3. En una tienda, cada producto tiene un precio y una cantidad disponible. Y un cliente tiene un carrito de compras donde puede agregar productos.
Cada que añade un producto al carrito, se debe calcular el total del costo de los productos en el carrito.

    - Crea un análisis, diagrama de clases y código que implemente la sobrecarga de operadores.
    - Debes crear al menos 2 productos diferentes y un cliente con un carrito de compras.

---
<!-- .slide: data-background-image="../../content/psg-bg-dark.png" data-background-size="100%"-->

<br>
<br>
<br>
<br>
<br>

[![GitHub](../../content/github_logo.png) <!-- .element width="20%"-->](https://github.com/python-la-paz/python-study-group-oop/content/sesion07)

Repositorio de la Sesión

---
<!--.slide: data-visibility="hidden"-->
## Bibliografía y Referencias

- [Duck Typing](https://coggle.it/diagram/aAEvbcfX6LrOExL8/t/duck-typing)
- [Qué es Duck Typing](https://codigonautas.com/que-es-duck-typing/)
- [Duck Typing en Python](https://keepcoding.io/blog/duck-typing-en-python/)
- [Duck Typing Python](https://ellibrodepython.com/duck-typing-python)
- [Polimorfismo en POO](https://desarrolloweb.com/articulos/polimorfismo-programacion-orientada-objetos-concepto.html)
- [Polimorfismo en Python](https://fredygeek.com/2025/04/23/polimorfismo-en-python-que-es-y-como-funciona-con-ejemplos-claros/)
- [Polimorfismo en Python](https://www.guru99.com/es/polymorphism-in-python.html)
- [Sobrecarga de operadores](https://docs.python.org/3/library/operator.html)
- [Python Operator Overloading](https://www.delftstack.com/es/howto/python/python-operator-overloading/)
- [Object Oriented Analysis](https://www.gyata.ai/es/object-oriented-programming/object-oriented-analysis)
- [Guía PEP 8](https://peps.python.org/pep-0008/#class-names)
- [Mermaid Charts](https://www.mermaidchart.com/play)
- [Draw.io](https://app.diagrams.net/)
- [Python 3 Object-oriented Programming, Second Edition, Dusty PhillipsDusty Phillips](https://github.com/PacktPublishing/Python-3-Object-Oriented-Programming-Second-Edition)
- [Enfoque orientado a objetos](https://1library.co/article/enfoque-orientado-a-objetos-base-te%C3%B3rica.qvld461y)
