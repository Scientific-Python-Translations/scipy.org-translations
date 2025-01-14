---
title: Dúvidas Frequentes (FAQ)
sidebar: false
---

## O que é a SciPy?

SciPy é um conjunto de ferramentas científicas e numéricas de código aberto (licença BSD) em Python. Atualmente suporta funções especiais, integração,
resolvedores de equações diferenciais ordinárias (ODE), otimização,
ferramentas paralelas de programação, um compilador de expressão para C++ para rápida execução
e outros. Uma boa regra geral é que se um algoritmo estiver descrito em
um livro didático sobre computação numérica (por exemplo, a conhecida série
Receitas Numéricas), provavelmente está implementado na SciPy.

## Quanto custa isso?

A SciPy está disponível gratuitamente. Ela é distribuida como software de código aberto (open source), o que significa que você tem acesso completo ao código e pode usá-lo de qualquer maneira que seja permitida pela licença liberal BSD.

## Quais são os termos da licença da SciPy?

A licença da SciPy é gratuita para uso comercial e não-comercial, pelos termos da [licença BSD](https://github.com/scipy/scipy/blob/main/LICENSE.txt).

## Como a SciPy pode ser rápida se é escrita em uma linguagem interpretada como Python?

Na verdade, os loops críticos que determinam o desempenho da biblioteca são normalmente implementados em C, C++ ou Fortran. Partes da SciPy são camadas finas de código desenvolvidas sobre as rotinas científicas
que estão livremente disponíveis em <https://www.netlib.org/>. Netlib
é um enorme repositório de algoritmos científicos incrivelmente valiosos e robustos de
escritos em C e Fortran. Não seria ideal reescrever estes algoritmos e trabalhar por anos para debugá-los. SciPy usa uma variedade de métodos
para gerar \"wrappers\" em torno desses algoritmos para que eles
possam ser usados em Python. Alguns wrappers foram gerados manualmente
em C. O restante foi gerado usando SWIG ou
[f2py](https://www.f2py.com). Algumas das contribuições mais recentes para SciPy
são ou escritas completamente ou estão empacotadas com
[Cython](https://cython.org/) ou [Pythran](https://pythran.readthedocs.io).

Uma segunda resposta é a seguinte: para problemas difíceis, um melhor algoritmo pode
fazer uma tremenda diferença no tempo necessário para resolver um problema.
Então, usar os algoritmos integrados da SciPy pode ser muito mais rápido do que um algoritmo
simples implementado em C.

## Encontrei um bug. O que devo fazer?

A equipe de desenvolvimento da SciPy trabalha duro para tornar a SciPy tão confiável quanto
possível, mas, como em qualquer produto de software, ocorrem erros. Se você encontrar
bugs que afetam seu software, por favor, nos informe abrindo uma issue no
o [rastreador de erros da SciPy](https://github.com/scipy/scipy/issues).

## Como posso me envolver com a SciPy?

Vá até nossa página [community](/community).
Estamos interessados em que mais pessoas ajudem a escrever código,
testes, documentação e a desenvolver nosso site.

## Existe apoio comercial disponível?

Sim, o suporte comercial é oferecido à SciPy por várias empresas,
por exemplo [Anaconda](https://www.anaconda.com),
[Enthought](https://www.enthought.com) e
[Quansight](https://www.quansight.com).

# NumPy vs. SciPy vs. outros pacotes

## Qual é a diferença entre NumPy e SciPy?

Em um mundo ideal, o NumPy não contém nada além do tipo de dados de array
e as operações mais básicas: indexação, ordenação, reformatação, funções elementares
básicas, etc. Todo código numérico deveria viver na SciPy.
No entanto, um dos objetivos importantes da NumPy é a compatibilidade, então a NumPy
tenta manter todos os recursos suportados por qualquer dos seus antecessores.
Assim, a NumPy contém algumas funções de álgebra linear e transformações de Fourier, embora fosse mais apropriado que estas funções pertencessem à SciPy. Em qualquer caso, a SciPy contém versões mais completas dos módulos de álgebra linear, bem como muitos outros algoritmos numéricos. Se você está fazendo computação científica
com Python, você deve provavelmente instalar tanto a NumPy
quanto a SciPy. A maioria dos novos recursos pertence à SciPy ao invés da NumPy.

## Como faço um gráfico usando a SciPy?

A funcionalidade de plotar gráficos vai além do escopo da SciPy, que
se concentra em objetos numéricos e algoritmos. Existem vários pacotes que podem ser integrados com a SciPy para produzir gráficos de alta qualidade,
como o imensamente popular [Matplotlib](https://matplotlib.org). Outras
opções populares são [Bokeh](https://bokeh.pydata.org/en/latest),
[Plotly](https://plot.ly) e [Altair](https://altair-viz.github.io).

## Como faço para fazer gráficos/visualizações em 3D usando a SciPy?

Assim como a produção de gráficos em 2D, os gráficos 3D estão além do escopo da SciPy. Tal como no caso do 2D, existem pacotes que podem ser integrados à SciPy para gerar esses gráficos.
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
