---
title: よくある質問と回答(FAQ)
sidebar: false
---

## SciPyとは？

SciPy は Python 用のオープンソース (BSD ライセンス) な科学計算ツール群です。 現時点で、SciPyは特殊関数や、数値積分、常微分方程式（ODE）ソルバー、勾配最適化、並列プログラミングツール、高速実行のためのC++トランスパイラなどをサポートしています。 ある一つの良い大まかな目安として、数値計算に関する一般的な教科書（例えば、有名な「Numerical Recipes」シリーズ）に載っている計算手法は、おそらくSciPyに実装されています。

## SciPyを使うのにどれくらいの費用がかかりますか？

SciPyは無料で利用できます。 SciPyはオープンソースソフトウェアとして配布されています。
つまり、誰でもソースコードにアクセスでき、比較的寛容なBSD ライセンスによって許されている条件下で
使用することができます。

## SciPyのライセンス条件とはどんなものですか？

SciPyのライセンスは、BSDライセンスの条件に従い、商用・非商用のどちらでも利用できます。
詳細は[こちら](https://github.com/scipy/scipy/blob/main/LICENSE.txt)をご参照ください。

## Pythonのようなインタープリター型言語で書かれているのに、SciPyはどのように高速な計算を実現しているのでしょうか？

実は、SciPyでは計算時間に大きな影響を与えるループ処理は通常、C、C++、またはFortranで実装されています。 実際の所、SciPyの一部のコードは、こちらにあるような既存の自由に利用できる科学計算ライブラリを薄くラップしただけのものもあります。 <https://www.netlib.org/> Netlib は、C および Fortran で書かれた非常に性能がが高く堅牢な、科学技術計算用アルゴリズムが集められた巨大なリポジトリです。 これらのコードやアルゴリズムを書き換えるのはあまり賢明ではなく、デバッグには何年もかかります。 SciPyでは、これらのコードの周りに「wrappers」を作ることにより、様々な
メソッドを使用できるようにしています。これにより、SciPyを使って、これらのメソッドはPythonから使用できるようになります。 SciPyのいくつかのラッパー部は、C言語のコードで
手動で生成されました。残りは、SWIGまたは
[f2py](https://www.f2py.com) を使用して生成されています。 SciPyに対する最近のコードでは、いくつかはPythonで全て書かれているか、
[Cython](https://cython.org/) または [Pythran](https://pythran.readthedocs.io) でラップされています。

二つ目の答えとしては、解くことが難しい問題に関してです。 より良いアルゴリズムは、
このような問題を解くのに時間に、大きな差をもたらします。
なので、SciPyが実装している賢いアルゴリズムを使用することで、C言語などで実装された単純な
アルゴリズムよりもはるかに高速に計算できるかもしれません。

## バグを見つけました。 どうすればいいでしょうか？

The SciPy development team works hard to make SciPy as reliable as
possible, but, as in any software product, bugs do occur. If you find
bugs that affect your software, please tell us by entering a ticket in
the [SciPy bug tracker](https://github.com/scipy/scipy/issues).

## How can I get involved in SciPy?

Head to our [community](/community) page.
We are keen for more people to help out writing code,
tests, documentation, and helping out with the website.

## Is there commercial support available?

Yes, commercial support is offered for SciPy by a number of companies,
for example [Anaconda](https://www.anaconda.com),
[Enthought](https://www.enthought.com), and
[Quansight](https://www.quansight.com).

# NumPy vs. SciPy vs. other packages

## What is the difference between NumPy and SciPy?

In an ideal world, NumPy would contain nothing but the array data type
and the most basic operations: indexing, sorting, reshaping, basic
elementwise functions, etc. All numerical code would reside in SciPy.
However, one of NumPy\'s important goals is compatibility, so NumPy
tries to retain all features supported by either of its predecessors.
Thus, NumPy contains some linear algebra functions and Fourier
transforms, even though these more properly belong in SciPy. In any
case, SciPy contains more fully-featured versions of the linear algebra
modules, as well as many other numerical algorithms. If you are doing
scientific computing with Python, you should probably install both NumPy
and SciPy. Most new features belong in SciPy rather than NumPy.

## How do I make plots using SciPy?

Plotting functionality is beyond the scope of SciPy, which
focus on numerical objects and algorithms. Several packages exist that
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
