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

La funcionalidad de gráficos está más allá del alcance de SciPy, el cual
se centra en objetos numéricos y algoritmos. Existen varios paquetes que se integran estrechamente con SciPy para producir gráficos de alta calidad, como el inmensamente popular [Matplotlib](https://matplotlib.org). Otros paquetes populares son [Bokeh](https://bokeh.pydata.org/en/latest),
[Plotly](https://plot.ly) y [Altair](https://altair-viz.github.io).

## ¿Cómo puedo hacer gráficos 3D/visualizaciones usando SciPy?

Al igual que el trazado en 2D, los gráficos 3D están más allá del alcance de SciPy, pero como en el caso 2D, existen paquetes que se integran con SciPy.
[Matplotlib](https://matplotlib.org) proporciona gráficos 3D básicos en el subpaquete `mplot3d`. mientras que [Mayavi](https://docs.enthought.com/mayavi/mayavi/) proporciona una amplia gama de características de visualización 3D de alta calidad, utilizando el potente motor [VTK](https://www.vtk.org/).

## ¿Por qué `numpy.linalg` y `scipy.linalg`? ¿Cuál es la diferencia?

`scipy.linalg` es un \"wrapper\" más completo de Fortran [LAPACK](https://www.netlib.org/lapack/) usando [f2py](https://www.f2py.com).

Uno de los objetivos de diseño de NumPy era hacerlo construible sin un compilador Fortran, y si usted no tiene LAPACK disponible, NumPy utilizará su propia implementación. SciPy requiere de un compilador Fortran para ser construido, y depende en gran medida de código Fortran envuelto.

Los módulos `linalg` en NumPy y SciPy tienen algunas funciones comunes pero con diferente documentación, y `scipy.linalg` contiene funciones no encontradas en `numpy.linalg`, tales como funciones relacionadas con la [descomposición LU](https://en.wikipedia.org/wiki/LU_decomposition) y la [descomposición de Schur](https://en.wikipedia.org/wiki/Schur_decomposition), múltiples maneras de calcular la pseudoinversa, y matrices transcendentes, como el [logaritmo de una matriz](https://en.wikipedia.org/wiki/Logarithm_of_a_matrix). Algunas funciones que existen en ambos han aumentado su funcionalidad en
`scipy.linalg`; por ejemplo, `scipy.linalg.eig` puede tomar una segunda matriz como argumento para resolver [problemas de eigenvalor generalizado](https://en.wikipedia.org/wiki/Generalized_eigenvalue_problem).

# Soporte de versiones de Python

## ¿Siguen NumPy y SciPy soportando Python 2.7?

La última versión de NumPy que soporta Python 2.7 es NumPy 1.16.x. La última versión de SciPy en hacerlo es SciPy 1.2.x. La primera versión de NumPy para soportar Python 3.x fue NumPy 1.5.0. El soporte para Python 3 en SciPy fue introducido en SciPy 0.9.0.

## ¿Funciona SciPy con PyPy?

En general, sí. Mejoras recientes en [PyPy](https://pypy.org) han hecho que la pila científica de Python funcione con PyPy. Since much of SciPy is
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
