<!-- .slide: data-background-image="../../content/psg-bg-dark.png" data-background-size="100%"-->
![Python La paz](../Logo.png) <!-- .element  hidden="true" -->

<br>
<br>
<br>

### Sesión  10
#### Patrones de Diseño
#### Factory

---

### Antes de empezar

---

#### Proyecto en VSCode

Abre el proyecto en VSCode

```bash
code psg-oop-2025
```

Crea una carpeta con el nombre `sesion10`

```bash
mkdir sesion10
cd sesion10
```

- Los archivos de esta sesión deben estar dentro de esta carpeta

- Al finalizar la sesión, sube los cambios al repositorio en un commit

---

#### ¿Qué es un patrón de diseño?

Un patrón de diseño es una **idea o solución** típica para resolver un problema

que se repite **una y otra vez**

---

Los patrones varían en complejidad y propósito y pueden ser clasificados en tres categorías principales:

- **Creacionales**: Se centran en la *creación* de objetos y clases
- **Estructurales**: Se centran en la *composición* de clases y objetos
- **De Comportamiento**: Se centran en la *interacción y responsabilidad* entre objetos

---

Nos enfocaremos en los **patrones creacionales**

que son los que nos ayudan a crear objetos de manera eficiente y flexible

---

#### Patrones Creacionales

Son aquellos que se encargan de la **creación** de objetos

Ofrecen enfoques estructurados y reutilizables para crear **instancias** de clases

los más comunes son:

- **Singleton**
- **Factory**

---

#### Factory

Llamado

**"metodo de fábrica"**

Es como tener una **fábrica** que crea **objetos diferentes** según las **necesidades**

---

> "El patrón Factory es como pedir en una **cafetería**: tú solo dices qué quieres, y alguien más se encarga de prepararlo por ti."

---

![Factory](./img/factory.gif)

---

#### ¿Por qué usar Factory?

- **Flexibilidad**: Permite crear diferentes tipos de objetos sin necesidad de conocer la clase exacta que se va a instanciar
- **Desacoplamiento**: Separa la lógica de creación de objetos de su uso
- **Mantenimiento**: Facilita la modificación y extensión del código sin afectar a las clases que lo utilizan

---
#### Ejemplos comunes

*Aplicaciones web y escritorio*

- **Creación de tipos de usuarios:** (administrador, cliente, etc.)
- **Generación de reportes:** (PDF, Excel, etc.)
- **Creación de notificaciones:** (correo electrónico, SMS, etc.)

---
#### Ejemplos comunes

*Juegos y simulaciones*

- **Creación de personajes:** (guerrero, mago, arquero, etc.)
- **Generación de enemigos:** (zombies, dragones, robots, etc.)
- **Creación de vehículos:** (coche, moto, avión, etc.)

---

#### Ejemplos comunes

*Seguridad y autenticación*

- **Generación de autenticación:** (Google, Facebook, GitHub, etc.)
- **Generación de permisos:** (lectura, escritura, ejecución, etc.)
- **Creación de autenticación biométrica:** (huella dactilar, reconocimiento facial, etc.)


---
#### Ejemplos comunes

*IoT y dispositivos inteligentes*

- **Estados de sensores:** (temperatura, humedad, luz, etc.)
- **Generación de dispositivos:** (termómetro, cámara, bombilla, etc.)
- **Generación de protocolos de comunicación:** (MQTT, HTTP, etc.)

---

#### Ventajas de usar Factory

- **Reutilización de código**: Permite reutilizar el código de creación de objetos en diferentes partes
- **Facilidad de mantenimiento**: Si se necesita cambiar la forma en que se crean los objetos, solo se modifica el Factory
- **Escalabilidad**: Facilita la adición de nuevos tipos de objetos sin afectar al código existente

---

#### Desventajas de usar Factory

- **Complejidad adicional**: Introduce una capa adicional de abstracción que puede hacer el código más complejo
- **Sobrecarga de rendimiento**: En algunos casos, la creación de objetos a través de un Factory puede ser menos eficiente que la creación directa
- **Granularidad**: Puede llevar a una sobreabundancia de clases y fábricas si no se gestiona adecuadamente

---

#### Diagrama de clases

1. definir las clases que van a participar en el patrón Factory
los productos que van a ser creados

````
```mermaid
classDiagram
    class Producto {
	    +usar()
    }
    class ProductoA {
	    +usar()
    }
    class ProductoB {
	    +usar()
    }
    Producto <|-- ProductoA
    Producto <|-- ProductoB
```
````

---
#### Diagrama de clases

Los productos A y B **heredan** de la clase Producto y serán creados por una fábrica

```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
direction LR
    class Producto {
	    +usar()
    }
    class ProductoA {
	    +usar()
    }
    class ProductoB {
	    +usar()
    }
    Producto <|-- ProductoA
    Producto <|-- ProductoB
```
<!--.element class="center-mermaid"-->
---

#### Diagrama de clases

2. Ahora definimos la clase **Fábrica** y las fábricas concretas que crearán los productos A y B

````
```mermaid
classDiagram
    class Fabrica {
	    +crear()
    }
    class FabricaA {
	    +crear()
    }
    class FabricaB {
	    +crear()
    }
    Fabrica <|-- FabricaA
    Fabrica <|-- FabricaB
```
````

---
#### Diagrama de clases

La FabricaA y FabricaB heredan de la clase Fabrica ambos crearan productos de tipo Producto

```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
direction LR
    class Fabrica {
	    +crear()
    }
    class FabricaA {
	    +crear()
    }
    class FabricaB {
	    +crear()
    }
    Fabrica <|-- FabricaA
    Fabrica <|-- FabricaB
```
<!--.element class="center-mermaid"-->

---
#### Diagrama de clases

3. Unimos las fábricas con los productos que crean se realiza mediante
una **relación de asociación**, donde la fábrica crea productos de tipo Producto

````
```mermaid
classDiagram
    class Producto {
	    +usar()
    }
    class ProductoA {
	    +usar()
    }
    class ProductoB {
	    +usar()
    }
    class Fabrica {
	    +crear() Producto
    }
    class FabricaA {
	    +crear() Producto
    }
    class FabricaB {
	    +crear() Producto
    }
    Producto <|-- ProductoA
    Producto <|-- ProductoB
    Fabrica <|-- FabricaA
    Fabrica <|-- FabricaB
    Fabrica --> Producto
```
````
---
#### Diagrama de clases

El diagrama final muestra la relación entre las fábricas y los productos que se  va a crear


```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
direction LR
    class Producto {
	    +usar()
    }
    class ProductoA {
	    +usar()
    }
    class ProductoB {
	    +usar()
    }
    class Fabrica {
	    +crear() Producto
    }
    class FabricaA {
	    +crear() Producto
    }
    class FabricaB {
	    +crear() Producto
    }
    Producto <|-- ProductoA
    Producto <|-- ProductoB
    Fabrica <|-- FabricaA
    Fabrica <|-- FabricaB
    Fabrica --> Producto
```
<!--.element class="center-mermaid"-->

---

#### Estructura de Factory en Python

**Factory** implementa **Herencia** y **polimorfismo** pilares de la programación orientada a objetos

La estructura de un Factory se puede ver mejor en un ejemplo **práctico**

---

#### Ejemplo 01

Crear los archivos `cafeteria.md` y `cafeteria.py` en la carpeta `sesion10`
```markdown
Una cafetería prepara Expresos y Cappuccinos,
el cliente (tú) solo debes pedir el tipo de café que desea
el barista utilizará las máquinas adecuadas para preparar el café
Todos los cafes se pueden tomar
Las cafeteras preparan un tipo de café, después son consumidos
por el cliente
Al ingresar salir se termina la ejecución
```


Se implementará el patrón Factory

---

Análisis

```markdown
# Análisis
Requisitos:
- Se preparan dos tipos de café: Expreso y Cappuccino
- El cliente solo debe pedir el tipo de café que desea
- Se utiliza la máquina adecuada para cada café
- Todos los cafés se pueden tomar
- Las cafeteras preparan un tipo de café
- Si se ingresa "salir" se termina la ejecución

Objetos:
- Café (Expreso, Cappuccino)
- Cafetera (CafeteraExpreso, CafeteraCappuccino)
- Barista

Características:
- Café: (sin características)
- Expreso: (Café)
- Cappuccino: (Café)
- Cafetera: (sin características)
- CafeteraExpreso: (Cafetera)
- CafeteraCappuccino: (Cafetera)
- Barista: (sin características)

Acciones:
- Café: tomar
- Expreso: tomar
- Cappuccino: tomar
- Cafetera: preparar
- CafeteraExpreso: preparar
- CafeteraCappuccino: preparar
- Barista: preparar cafe
```

---
#### Diagrama de clases

````
```mermaid
classDiagram
    class Cafe {
        +tomar()
    }
    class Expreso {
        +tomar()
    }
    class Cappuccino {
        +tomar()
    }
    class Cafetera {
        +preparar()
    }
    class CafeteraExpreso {
        +preparar()
    }
    class CafeteraCappuccino {
        +preparar()
    }
    class Barista {
        +preparar_cafe()
    }
    Cafe <|-- Expreso
    Cafe <|-- Cappuccino
    Cafetera <|-- CafeteraExpreso
    Cafetera <|-- CafeteraCappuccino
    Cafetera --> Cafe
    Barista --> Cafetera
```
````

---
#### Diagrama de clases

```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"  }}%%
classDiagram
direction LR
    class Cafe {
        +tomar()
    }
    class Expreso {
        +tomar()
    }
    class Cappuccino {
        +tomar()
    }
    class Cafetera {
        +preparar()
    }
    class CafeteraExpreso {
        +preparar()
    }
    class CafeteraCappuccino {
        +preparar()
    }
    class Barista {
        +preparar_cafe()
    }
    Cafe <|-- Expreso
    Cafe <|-- Cappuccino
    Cafetera <|-- CafeteraExpreso
    Cafetera <|-- CafeteraCappuccino
    Cafetera --> Cafe
    Barista --> Cafetera
```
<!--.element class="center-mermaid"-->

---
#### Implementación en Python

Primero definimos la clase base `Cafe` y las clases derivadas `Expreso` y `Cappuccino`

```python
class Cafe:
    def tomar(self):
        print("Tomando un café")

class Expreso(Cafe):
    def tomar(self):
        print("☕ Tomando un expreso")

class Cappuccino(Cafe):
    def tomar(self):
        print("🥛 Tomando un cappuccino")
```

---
Luego definimos la clase base `Cafetera` y las clases derivadas `CafeteraExpreso` y `CafeteraCappuccino`

```python
class Cafetera:
    def preparar(self):
        pass
class CafeteraExpreso(Cafetera):
    def preparar(self):
        return Expreso()
class CafeteraCappuccino(Cafetera):
    def preparar(self):
        return Cappuccino()
```

---
Definimos las clases `Barista` que interactúa con las cafeteras

```python
class Barista:
    def preparar_cafe(self, tipo):
        if tipo == "expreso":
            return CafeteraExpreso().preparar()
        if tipo == "cappuccino":
            return CafeteraCappuccino().preparar()
        raise ValueError("❌ Café no disponible. Intente de nuevo")
```

---
Finalmente creamos la lógica donde como clientes pedimos el **café** al barista

```python
while True:
    tipo_cafe = input("💬 ¿Qué café desea? (expreso/cappuccino/salir): ")
    tipo_cafe = tipo_cafe.lower().strip()
    if tipo_cafe == "salir":
        print("🚶‍♂️ Saliendo de la cafetería.")
        break
    try:
        barista = Barista()
        cafe = barista.preparar_cafe(tipo_cafe)
        cafe.tomar()
    except ValueError as e:
        print(e)
```


---
#### Código completo

```python
# Productos
class Cafe:
    def tomar(self):
        print("Tomando un café")

class Expreso(Cafe):
    def tomar(self):
        print("☕ Tomando un expreso")

class Cappuccino(Cafe):
    def tomar(self):
        print("🥛 Tomando un cappuccino")

# Fabricas
class Cafetera:
    def preparar(self):
        pass
class CafeteraExpreso(Cafetera):
    def preparar(self):
        return Expreso()
class CafeteraCappuccino(Cafetera):
    def preparar(self):
        return Cappuccino()

# Factory Central (decide qué fábrica usar)
class Barista:
    def preparar_cafe(self, tipo):
        if tipo == "expreso":
            return CafeteraExpreso().preparar()
        if tipo == "cappuccino":
            return CafeteraCappuccino().preparar()
        raise ValueError("❌ Café no disponible. Intente de nuevo")

# Cliente (No conoce las fábricas, solo pide el café)
while True:
    tipo_cafe = input("💬 ¿Qué café desea? (expreso/cappuccino/salir): ")
    tipo_cafe = tipo_cafe.lower().strip()
    if tipo_cafe == "salir":
        print("🚶‍♂️ Saliendo de la cafetería.")
        break
    try:
        barista = Barista()
        cafe = barista.preparar_cafe(tipo_cafe)
        cafe.tomar()
    except ValueError as e:
        print(e)
```

---

#### Ejecución

```bash
python cafeteria.py
```

```text
💬 ¿Qué café desea? (expreso/cappuccino/salir): expreso
☕ Tomando un expreso
💬 ¿Qué café desea? (expreso/cappuccino/salir): cappuccino
🥛 Tomando un cappuccino
💬 ¿Qué café desea? (expreso/cappuccino/salir): latte
❌ Café no disponible. Intente de nuevo
💬 ¿Qué café desea? (expreso/cappuccino/salir): salir
🚶‍♂️ Saliendo de la cafetería.
```

---

En el ejemplo anterior se muestra cómo el patrón Factory
permite **crear diferentes** tipos de café sin que el cliente 
conozca los detalles de la creación

---

El único que conoce los detalles de la creación es el **Barista**
que utiliza las **fábricas adecuadas** para preparar el café solicitado

---

#### Ejercicio para ti (02)

Crea los archivos `juego.md` y `juego.py` en la carpeta `sesion10`

Obtener el *Análisis*

---


```markdown
En un juego de rol, los jugadores pueden elegir diferentes
tipos de armas.
Cuando un jugador solicita un arma, el armero utiliza
la herramienta adecuada para crearla
Cada herramienta crea un solo tipo de arma:
- El martillo crea espadas
- La Sierra crea arcos
Todas las armas pueden usarse para atacar
Si el jugador escribe "salir" en lugar de un tipo de arma,
el programa finaliza.
```

3 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

---

#### Análisis

```markdown
Requisitos:
- Hay dos tipos de armas: Espada y Arco.
- El jugador solo debe pedir el tipo de arma que desea.
- Se usa la herramienta adecuada para fabricar cada arma.
- Todas las armas pueden usarse para atacar.
- Cada herramienta fabrica un tipo de arma.
- Si se ingresa "salir" se termina la ejecución.

Objetos:
- Arma (Espada, Arco)
- Herramienta (Martillo, Sierra)
- Armero

Características:
- Arma: (sin características extra)
- Espada: (Arma)
- Arco: (Arma)
- Herramienta: (sin características)
- Martillo: (Herramienta)
- Sierra: (Herramienta)
- Armero: (sin características)

Acciones:
- Arma: atacar()
- Espada: atacar()
- Arco: atacar()
- Herramienta: fabricar()
- Martillo: fabricar()
- Sierra: fabricar()
- Armero: (sin acciones)
```

---

#### Ejercicio para ti (02)

Ahora obtenemos el diseño del *diagrama de clase*

2 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Modifica el archivo `juego.md`

---

#### Diagrama de clases

````
```mermaid
classDiagram
    class Arma {
        +atacar()
    }
    class Espada {
        +atacar()
    }
    class Arco {
        +atacar()
    }
    class Herramienta {
        +fabricar()
    }
    class Martillo {
        +fabricar()
    }
    class Sierra {
        +fabricar()
    }
    class Armero {
    }
    Arma <|-- Espada
    Arma <|-- Arco
    Herramienta <|-- Martillo
    Herramienta <|-- Sierra
    Herramienta --> Arma
    Armero --> Herramienta
```
````


---

#### Diagrama de clases

```mermaid
%%{init: {"theme": "dark", "look": "handDrawn"}}%%
classDiagram
direction LR
    class Arma {
        +atacar()
    }
    class Espada {
        +atacar()
    }
    class Arco {
        +atacar()
    }
    class Herramienta {
        +fabricar()
    }
    class Martillo {
        +fabricar()
    }
    class Sierra {
        +fabricar()
    }
    class Armero {
        +fabricar_arma()
    }
    Arma <|-- Espada
    Arma <|-- Arco
    Herramienta <|-- Martillo
    Herramienta <|-- Sierra
    Herramienta --> Arma
    Armero --> Herramienta
```
<!--.element class="center-mermaid"-->


---

#### Ejercicio para ti (02)

Ya tenemos el *análisis y diseño* de la clase

Ahora podemos **programar**

Modifica el archivo `juego.py`

2 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Primero implementamos las armas

---

Clases de las armas

```python
class Arma:
    def atacar(self):
        print("Atacando con un arma")

class Espada(Arma):
    def atacar(self):
        print("🗡️ Atacando con una espada")

class Arco(Arma):
    def atacar(self):
        print("🏹 Atacando con un arco")
```


---

Segundo implementamos las herramientas que fabrican las armas

2 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Modifica el archivo `juego.py`

---
```python
class Herramienta:
    def fabricar(self):
        pass

class Martillo(Herramienta):
    def fabricar(self):
        return Espada()

class Sierra(Herramienta):
    def fabricar(self):
        return Arco()
```

---

#### Implementación del Armero

Tercero implementar el Armero que utiliza las herramientas para fabricar las armas

2 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

Modifica el archivo `juego.py`

---

```python
class Armero:
    def fabricar_arma(self, tipo):
        if tipo == "espada":
            return Martillo().fabricar()
        if tipo == "arco":
            return Sierra().fabricar()
        raise ValueError("❌ Arma no disponible. Intente de nuevo")
```

---

#### Interacción del jugador

Ahora que tenemos el Armero, implementar la lógica del juego donde el jugador solicita un arma
al armero y si ingresa "salir" se termina la ejecución

2 minutos

<iframe src="https://time-stuff.com/embed.html" frameborder="0" scrolling="no" width="391" height="140"></iframe>

---

```python
while True:
    tipo_arma = input("💬 ¿Qué arma desea? (espada/arco/salir): ")
    tipo_arma = tipo_arma.lower().strip()
    if tipo_arma == "salir":
        print("🚶‍♂️ Saliendo del juego.")
        break
    try:
        armero = Armero()
        arma = armero.fabricar_arma(tipo_arma)
        arma.atacar()
    except ValueError as e:
        print(e)
```

---

#### Código completo

```python
class Arma:
    def atacar(self):
        print("Atacando con un arma")

class Espada(Arma):
    def atacar(self):
        print("🗡️ Atacando con una espada")

class Arco(Arma):
    def atacar(self):
        print("🏹 Atacando con un arco")

class Herramienta:
    def fabricar(self):
        pass

class Martillo(Herramienta):
    def fabricar(self):
        return Espada()

class Sierra(Herramienta):
    def fabricar(self):
        return Arco()

class Armero:
    def fabricar_arma(self, tipo):
        if tipo == "espada":
            return Martillo().fabricar()
        if tipo == "arco":
            return Sierra().fabricar()
        raise ValueError("❌ Arma no disponible. Intente de nuevo")

while True:
    tipo_arma = input("💬 ¿Qué arma desea? (espada/arco/salir): ")
    tipo_arma = tipo_arma.lower().strip()
    if tipo_arma == "salir":
        print("🚶‍♂️ Saliendo del juego.")
        break
    try:
        armero = Armero()
        arma = armero.fabricar_arma(tipo_arma)
        arma.atacar()
    except ValueError as e:
        print(e)
```

---

#### Ejecución

```bash
python juego.py
```

```text
💬 ¿Qué arma desea? (espada/arco/salir): espada
🗡️ Atacando con una espada
💬 ¿Qué arma desea? (espada/arco/salir): arco
🏹 Atacando con un arco
💬 ¿Qué arma desea? (espada/arco/salir): hacha
❌ Arma no disponible. Intente de nuevo
💬 ¿Qué arma desea? (espada/arco/salir): salir
🚶‍♂️ Saliendo del juego.
```

---

Subimos los avances de la sesión al repositorio en **GitHub**

```bash
git add .
git commit -m "Sesión 10"
git push origin main
```

---

#### Resumen

- Un patrón de diseño es una solución típica para resolver problemas recurrentes en el desarrollo de software.
- Los patrones de diseño se clasifican en creacionales, estructurales y de comportamiento según su propósito.
- Los patrones creacionales ayudan a crear objetos de manera eficiente y flexible.

---

- El patrón Factory pertenece a los patrones creacionales y permite crear diferentes tipos de objetos según las necesidades.
- El patrón Factory aporta flexibilidad, desacoplamiento y facilidad de mantenimiento al separar la lógica de creación de objetos de su uso.
- El patrón Factory facilita la reutilización de código, la escalabilidad y el mantenimiento al permitir modificar la forma de crear objetos sin afectar el resto del código.

---

- El uso del patrón Factory puede agregar complejidad adicional y sobrecarga de rendimiento, y puede llevar a una sobreabundancia de clases si no se gestiona adecuadamente.
- El patrón Factory se representa en diagramas de clases mediante la relación entre fábricas y productos, mostrando herencia y asociación.
- La estructura del patrón Factory en Python utiliza herencia y polimorfismo para definir fábricas y productos.

---

- El análisis de requisitos, características y acciones es fundamental para diseñar correctamente las clases y sus relaciones al aplicar el patrón Factory.
- Los diagramas de clases ayudan a visualizar la estructura y relaciones entre fábricas y productos en el patrón Factory.
- El patrón Factory permite crear objetos sin que el cliente conozca los detalles de la creación, delegando esa responsabilidad a una fábrica especializada.


---

#### Retos

Crear una carpeta con el nombre "retos_sesion_10" dentro del proyecto en la raíz, en la cual por cada ejercicio debes crear los siguientes archivos:

```bash
# Estructura de carpetas
psg-oop-2025/
    retos_sesion_10/
        ejercicio_01.md
        ejercicio_01.py
        ejercicio_02.md
        ejercicio_02.py
```

---

1. Utilizando el patrón **Factory**

En una heladería, los clientes pueden pedir helados de **vainilla** o **chocolate**.  
Además, pueden elegir si desean su helado en **cono** o en **vaso**.  

El encargado utiliza la **máquina adecuada** para preparar cada sabor:

- La *máquina de vainilla* solo prepara helados de vainilla.  
- La *máquina de chocolate* solo prepara helados de chocolate.

Todos los helados comparten características en común:  
- Se pueden **comer**.  
- Tienen un **envase** (cono o vaso).

El sistema debe permitir al usuario realizar pedidos de helado mediante un **Factory**, y escribir `"salir"` para terminar el proceso.

*(1/4)*

---

- Los helados se representan como:

`"[sabor] 🍦 en [envase]"`

- El menú de opciones se representa como:

```text
🍨 Pedidos de Helado 🍨
1. Vainilla en Cono
2. Vainilla en Vaso
3. Chocolate en Cono
4. Chocolate en Vaso
Escribe "salir" para terminar.
```

*(2/4)*

---

El sistema debe permitir:

Crear helados mediante una **fábrica**

Representar cada helado en el formato especificado.

Registrar varios pedidos hasta que el usuario escriba "salir".

*(3/4)*

---

Instrucciones:

- Realiza el **análisis** y **diagrama de clases** para las clases `Helado`, `HeladoVainilla`, `HeladoChocolate`, `Maquina`, `MaquinaVainilla`, `MaquinaChocolate` en `ejercicio_01.md`
- Escribe el código en Python implementando el patrón Factory en `ejercicio_01.py`
- Prueba varios pedidos de helado para verificar el correcto funcionamiento

*(4/4)*

---

2. Utilizando el patrón **Factory**

Simulador de Batalla de Monstruos

Dos jugadores pueden elegir un **monstruo** para luchar.  
Cada jugador selecciona uno de los siguientes tipos:

- **Dragón**
- **Zombi**
- **Vampiro**

*(1/5)*

---

Cada monstruo tiene fortalezas y debilidades:

```markdown
- Dragón:
  - Fuerte contra Zombi
  - Débil contra Vampiro
  - Igual contra Dragón
- Zombi:
  - Fuerte contra Vampiro
  - Débil contra Dragón
  - Igual contra Zombi
- Vampiro:
  - Fuerte contra Dragón
  - Débil contra Zombi
  - Igual contra Vampiro
```

El simulador debe determinar el **resultado de la batalla** entre los monstruos elegidos, si alguno de los jugadores escribe `"salir"`, el juego termina.

*(2/5)*

---


Los monstruos se representan como:

`"[monstruo] 🧟‍♂️ listo para luchar"`

El menú de selección se representa como:

```text
🧩 Selección de Monstruos 🧩
Jugador 1: Elige tu monstruo (dragón/zombi/vampiro):
Jugador 2: Elige tu monstruo (dragón/zombi/vampiro):
Escribe "salir" para terminar.
```

*(3/5)*

---

El sistema debe permitir:

- Crear monstruos mediante una **fábrica**
- Representar cada monstruo en el formato especificado.
- Determinar el resultado de la batalla según las fortalezas y debilidades.
- Registrar varias batallas hasta que un jugador escriba "salir".

*(4/5)*

---

Instrucciones:

- Realiza el **análisis** y **diagrama de clases** para las clases `Monstruo`, `Dragon`, `Zombi`, `Vampiro`, `Spawner`, `SpawnerDragon`, `SpawnerZombi`, `SpawnerVampiro` en `ejercicio_02.md`
- Escribe el código en Python implementando el patrón Factory en `ejercicio_02.py`
- Prueba las batallas entre diferentes monstruos para verificar el correcto funcionamiento

*(5/5)*

---
<!-- .slide: data-background-image="../../content/psg-bg-dark.png" data-background-size="100%"-->

<br>
<br>
<br>
<br>
<br>

[![GitHub](../../content/github_logo.png) <!-- .element width="20%"-->](https://github.com/python-la-paz/python-study-group-oop/tree/main/content/sesion10)

Repositorio de la Sesión

---
<!--.slide: data-visibility="hidden"-->
## Bibliografía y Referencias

- [Factory Method](https://refactoring.guru/es/design-patterns/factory-method)
- [Patrón Factory Method Introducción y ejemplos](https://revistacompleta.com/patron-factory-method-introduccion-y-ejemplos/)
- [05-FactoryPattern](https://uetitc.github.io/ProgrammingII-2024-2/Lessons/05-FactoryPattern.html)
- [Factory Pattern](https://www.chucksacademy.com/es/topic/javascript-design-patterns/factory-pattern)
- [Object Oriented Analysis](https://www.gyata.ai/es/object-oriented-programming/object-oriented-analysis)
- [Diagrama de clases](https://diagramasuml.com/diagrama-de-clases/)
- [Guía PEP 8](https://peps.python.org/pep-0008/#class-names)
- [Mermaid Charts](https://www.mermaidchart.com/play)
- [Draw.io](https://app.diagrams.net/)
- [Python 3 Object-oriented Programming, Second Edition, Dusty Phillips](https://github.com/PacktPublishing/Python-3-Object-Oriented-Programming-Second-Edition)

