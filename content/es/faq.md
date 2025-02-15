---
title: aqPreguntas Frecuentes (Faq)
sidebar: false
---

## ¿Qué es SciPy?

SciPy es un conjunto de herramientas científicas y numéricas
de código abierto (licencia BSD) para Python. Actualmente soporta funciones especiales, integración, solucionadores de ecuaciones diferenciales ordinarias (ODE), optimización gradiente, herramientas de programación en paralelo, un compilador expresión-a-C++ para rápida ejecución, entre otros. Como regla general es que si está cubierto en
un libro de texto general sobre computación numérica (por ejemplo, la conocida serie Numerical Recipes), probablemente está implementado en SciPy.

## ¿Cuánto cuesta?

SciPy está disponible libremente. Se distribuye como software de código abierto,
significa que tienes acceso completo al código fuente y puedes usarlo
de cualquier forma permitida por su licencia liberal de BSD.

## ¿Cuáles son los términos de licencia de SciPy?

La licencia de SciPy es gratuita tanto para uso comercial como no comercial, por
los términos de la licencia BSD
[here](https://github.com/scipy/scipy/blob/main/LICENSE.txt).

## ¿Cómo puede SciPy ser rápido si está escrito en un lenguaje interpretado como Python?

En realidad, los bucles de tiempo crítico generalmente se implementan en C, C++, o
Fortran. Las partes de SciPy son capas delgadas de código encima de rutinas científicas
que están disponibles libremente en <https://www.netlib.org/>. Netlib es un enorme repositorio de algoritmos científicos increíblemente valiosos y robustos escritos en C y Fortran. Sería absurdo reescribir estos algoritmos y tomaría años depurarlos. SciPy utiliza una variedad de métodos para generar \"wrappers\" alrededor de estos algoritmos para que puedan ser usados en Python. Algunos \"wrappers\" fueron generados al codificarlos a mano
en C. El resto fueron generados usando ya sea SWIG o
[f2py](https://www.f2py.com). Algunas de las nuevas contribuciones a SciPy
están escritas enteramente o envueltas con
[Cython](https://cython.org/) o [Pythran](https://pythran.readthedocs.io).

Una segunda respuesta es que para problemas difíciles un mejor algoritmo puede
marcar una tremenda diferencia en el tiempo que tarda en resolver un problema.
Por lo tanto, el uso de los algoritmos incorporados de SciPy puede ser mucho más rápido que un simple algoritmo codificado en C.

## He encontrado un fallo. ¿Qué hago?

El equipo de desarrollo de SciPy trabaja duro para hacer a SciPy tan confiable como sea posible, pero, como en cualquier producto de software, los fallos ocurren. Si encuentras fallos que afecten al software por favor háznoslo saber creando un ticket en el [seguimiento de fallos de SciPy](https://github.com/scipy/scipy/issues).

## ¿Cómo puedo involucrarme en SciPy?

Ve a nuestra página [community](/community).
Estamos interesados en que más personas ayuden a escribir código,
pruebas, documentación y ayuda en el sitio web.

## ¿Hay soporte comercial disponible?

Sí, una serie de empresas ofrecen apoyo comercial para SciPy,
por ejemplo [Anaconda](https://www.anaconda.com),
[Enthought](https://www.enthought.com),
[Quansight](https://www.quansight.com).

# NumPy vs. SciPy vs. otros paquetes

## ¿Cuál es la diferencia entre NumPy y SciPy?

En un mundo ideal, NumPy no contendría más que el tipo de datos del arreglo y las operaciones más básicas: indexar, ordenar, remodelar, funciones básicas
elementales, etc. Todo el código numérico residiría en SciPy.
Sin embargo, uno de los objetivos importantes de NumPy es la compatibilidad, por lo que NumPy intenta retener todas las características soportadas por cualquiera de sus predecesores.
Así, NumPy contiene algunas funciones de álgebra lineal y transformadas de Fourier, aunque estas pertenecen más correctamente a SciPy. En cualquier caso, SciPy contiene versiones más completas de los módulos de álgebra lineal, así como muchos otros algoritmos numéricos. Si estás haciendo computación científica con Python, probablemente deberías instalar tanto NumPy como SciPy. La mayoría de las nuevas características pertenecen a SciPy en lugar de NumPy.

## ¿Cómo hago gráficos usando SciPy?

La graficación está más allá del alcance de SciPy, el cual
se centra en objetos numéricos y algoritmos. Several packages exist that
integrate closely with SciPy to produce high quality plots,
such as the immensely popular [Matplotlib](https://matplotlib.org). Other
popular options are [Bokeh](https://bokeh.pydata.org/en/latest),
[Plotly](https://plot.ly) and [Altair](https://altair-viz.github.io).

## How do I make 3D plots/visualizations using SciPy?

Like 2D plotting, 3D graphics is beyond the scope of SciPy,
but just as in the 2D case, packages exist that integrate with SciPy.
[Matplotlib](https://matplotlib.org) provides basic 3D plotting in the
`mplot3d` subpackage, whereas
[Mayavi](https://docs.enthought.com/mayavi/mayavi/) provides a wide
range of high-quality 3D visualization features, utilizing the powerful
[VTK](https://www.vtk.org/) engine.

## Why both `numpy.linalg` and `scipy.linalg`? What\'s the difference?

`scipy.linalg` is a more complete wrapping
of Fortran [LAPACK](https://www.netlib.org/lapack/) using
[f2py](https://www.f2py.com).

One of the design goals of NumPy was to make it buildable without a
Fortran compiler, and if you don\'t have LAPACK available, NumPy will
use its own implementation. SciPy requires a Fortran compiler to be
built, and heavily depends on wrapped Fortran code.

The `linalg` modules in NumPy and SciPy
have some common functions but with different docstrings, and
`scipy.linalg` contains functions not
found in `numpy.linalg`, such as functions
related to LU
decomposition and the
Schur
decomposition,
multiple ways of calculating the pseudoinverse, and matrix
transcendentals, like the matrix
logarithm. Some
functions that exist in both have augmented functionality in
`scipy.linalg`; for example,
`scipy.linalg.eig` can take a second
matrix argument for solving generalized eigenvalue
problems.

# Python version support

## Do NumPy and SciPy still support Python 2.7?

The last version of NumPy to support Python 2.7 is NumPy 1.16.x. The
last SciPy version to do so is SciPy 1.2.x. The first release of NumPy
to support Python 3.x was NumPy 1.5.0. Python 3 support in SciPy was
introduced in SciPy 0.9.0.

## Does SciPy work with PyPy?

In general, yes. Recent improvements in [PyPy](https://pypy.org) have
made the scientific Python stack work with PyPy. Since much of SciPy is
implemented as C
extension modules, the code may not run any faster (for most cases it\'s
significantly slower still, however, PyPy is actively working on
improving this). As always when benchmarking, your experience is the
best guide.

## Does SciPy work with Jython or C\#/.NET?

No, neither is supported. Jython never worked, because it runs on top of
the Java Virtual Machine and has no way to interface with extensions
written in C for the standard Python (CPython) interpreter.

Some years ago, there was an effort to make NumPy and SciPy compatible
with .NET. Some users at the time reported success in using NumPy with
[Ironclad](https://code.google.com/archive/p/ironclad) on 32-bit
Windows. Lastly, [Pyjion](https://www.trypyjion.com) is a new project which
reportedly could work with SciPy.

In any case, these runtime/compilers are out of scope of SciPy and not
officially supported by the development team.

# Where to get help

See the [community](/community) page.
