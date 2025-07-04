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
