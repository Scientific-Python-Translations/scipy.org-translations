---
title: Instalación
sidebar: false
---

{{< admonition tip >}}
Esta página asume que te acomoda usar una terminal y quieres de aprender
cómo usar un gestor de paquetes. Si eres principiante y solo quieres empezar
con SciPy tan pronto como sea posible, dale un vistazo a [la guía de instalación para principiantes](./beginner-install.md).
Si te acomoda usar una terminal y te interesa aprender
a utilizar un gestor de paquetes, ¡échale un vistazo a
[la guía principal de instalación](./install.md)!

El método recomendado para instalar SciPy depende de tu flujo de trabajo preferido.
Los flujos de trabajo más comunes se pueden dividir aproximadamente en las siguientes categorías:

- [Basado en proyectos (por ejemplo, `uv`, `pixi`)](#project-based) (recomendado para nuevos usuarios)
- [Basado en entornos (por ejemplo, `pip`, `conda`)](##environment-based) (el flujo de trabajo tradicional)
- [Administradores de paquetes del sistema](#system-package-managers) (no recomendado)
- [Compilación desde el código fuente](#building-from-source) (para depuración y desarrollo)

Para instalar SciPy con \[archivos de tipado], consulte [Instalación con archivos de tipado](#type-stubs).

[static type stubs]: https://typing.readthedocs.io/en/latest/guides/libraries.html

{{< admonition tip >}}
Installing type stubs may be required for
Interactive Development Environments (IDEs) to provide accurate type hints.
Si te acomoda usar una terminal y te interesa aprender
a utilizar un gestor de paquetes, ¡échale un vistazo a
[la guía principal de instalación](./install.md)!

{{< tabs >}}

[[tab]]
name = 'Project Based'
content = ''' <a name="project-based"></a>

### Installing with uv

Here is a step-by-step guide to setting up a project to use SciPy, with uv, a Python package manager.

1. Install `uv` following, [the instructions in the uv documentation](https://docs.astral.sh/uv/getting-started/installation/).

2. Cree un nuevo proyecto en un nuevo subdirectorio, ejecutando el siguiente comando en una terminal:

```bash
uv init try-scipy
cd try-scipy
```

{{< admonition hint >}}
El segundo comando cambia el directorio al directorio de su proyecto.
Si te acomoda usar una terminal y te interesa aprender
a utilizar un gestor de paquetes, ¡échale un vistazo a
[la guía principal de instalación](./install.md)!

3. Cree un nuevo proyecto en un nuevo subdirectorio, ejecutando el siguiente comando en una terminal:

```bash
uv add scipy
```

{{< admonition note >}}
¡Esto instalará Python automáticamente si aún no lo tiene instalado!
Si te acomoda usar una terminal y te interesa aprender
a utilizar un gestor de paquetes, ¡échale un vistazo a
[la guía principal de instalación](./install.md)!

{{< admonition tip >}}
Puede instalar otras librerías de Python de la misma manera, por ejemplo

```bash
uv add matplotlib
```

Si te acomoda usar una terminal y te interesa aprender
a utilizar un gestor de paquetes, ¡échale un vistazo a
[la guía principal de instalación](./install.md)!

4. ¡Pruebe SciPy!

```bash
uv run python
```

This will launch a Python interpreter session, from which you can `import scipy`.

<!-- prettier-ignore-end -->

Consulte los siguientes pasos en [la guía del usuario de SciPy][scipy-user-guide].

[scipy-user-guide]: https://docs.conda.io/projects/conda/en/latest/index.html

Los pasos para instalar SciPy desde [conda-forge] usando la herramienta de administración de paquetes [`pixi`] son ​​muy similares a los pasos para `uv`:

Después de reiniciar su computadora, querrá navegar al directorio de su proyecto `try-scipy` y ejecutar `uv run python` para volver a un intérprete de Python con SciPy disponible para su uso.
Para ejecutar un script de Python, puede usar `uv run myscript.py`.

Lea más en \[la guía de `uv` para trabajar en proyectos]\[uv-proyects].

[uv-projects]: https://docs.astral.sh/uv/guides/projects/

Si te acomoda usar una terminal y te interesa aprender
a utilizar un gestor de paquetes, ¡échale un vistazo a
[la guía principal de instalación](./install.md)!

### Instalando con `pixi`

Si trabaja con paquetes que no son de Python, es posible que prefiera instalar SciPy como un paquete de [Conda], de modo que pueda usar el mismo flujo de trabajo para paquetes que no están disponibles en [PyPI](https://pypi.org/), el índice de paquetes de Python.
Conda puede administrar paquetes en cualquier lenguaje, por lo que puede usarlo para instalar Python, compiladores y otros lenguajes.

[Conda]: https://docs.conda.io/projects/conda/en/latest/index.html

Los pasos para instalar SciPy desde [conda-forge] usando la herramienta de administración de paquetes [`pixi`] son ​​muy similares a los pasos para `uv`:

[conda-forge]: https://conda-forge.org/
[`pixi`]: https://pixi.sh/latest/

1. Instale `pixi`, siguiendo [las instrucciones en la documentación de `pixi`][install-pixi].

[install-pixi]: https://pixi.sh/latest/

2. Cree un nuevo proyecto en un nuevo subdirectorio:

```bash
pixi init try-scipy
cd try-scipy
```

3. Cree un nuevo proyecto en un nuevo subdirectorio, ejecutando el siguiente comando en una terminal:

```bash
pixi add scipy
```

4. ¡Pruebe SciPy!

```bash
pixi run python
```

'''

[[tab]]
name = 'Environment Based'
content = ''' <a name="environment-based"></a>

En los flujos de trabajo basados ​​en proyectos, un proyecto es un directorio que contiene un archivo que describe el proyecto, un archivo que describe las dependencias exactas del proyecto y los entornos (potencialmente múltiples) del proyecto.

Por el contrario, en los flujos de trabajo basados ​​en entornos, usted instala paquetes en un entorno, que puede activar y desactivar desde cualquier directorio.
Estos flujos de trabajo están bien establecidos, pero carecen de algunos beneficios de reproducibilidad de los flujos de trabajo basados ​​en proyectos.

### Instalando con `pip`

<!-- prettier-ignore-start -->

1. [Instale Python](https://www.python.org/downloads/).

2. Crea y activa un entorno virtual con `venv`.

{{< admonition hint >}}
Consulte [el tutorial en la Guía del usuario de empaquetado de Python](https://packaging.python.org/en/latest/tutorials/installing-packages/#creating-virtual-environments).
Si te acomoda usar una terminal y te interesa aprender
a utilizar un gestor de paquetes, ¡échale un vistazo a
[la guía principal de instalación](./install.md)!

3. Instala SciPy, utilizando [`pip`]:

```bash
python -m pip install scipy
```

<!-- prettier-ignore-end -->

[`pip`]: https://pip.pypa.io/es/stable/getting-started/

### Instalando con `conda`

[Miniforge] es la forma recomendada de instalar `conda` y [`mamba`], dos administradores de entorno basados ​​en Conda.
Después de crear un entorno, puede instalar SciPy desde conda-forge de la siguiente manera:

```bash
conda install scipy # or
mamba install scipy
```

[Miniforge]: https://conda-forge.org/download/
[`mamba`]: https://mamba.readthedocs.io/es/latest/

'''

[[tab]]
name = 'Package Manager'
content = ''' <a name="system-package-managers"></a>

## Instalación con archivos de tipado

Los administradores de paquetes del sistema pueden instalar los paquetes de Python más comunes.
Instalan paquetes para toda la computadora, a menudo usan versiones anteriores y no tienen tantas versiones disponibles. No son el método de instalación recomendado.

### Ubuntu y Debian

Usando `apt-get`:

```bash
sudo apt-get install python3-scipy
```

### Fedora

Usando `dnf`:

```bash
sudo dnf install python3-scipy
```

### macOS

macOS no tiene un administrador de paquetes preinstalado, pero puedes instalar [Homebrew](https://brew.sh/) y usarlo para instalar SciPy (y el propio Python):

```bash
brew install scipy
```

'''

[[tab]]
name = 'Building from Source'
content = ''' <a name="building-from-source"></a>

A word of warning: building SciPy from source can be a nontrivial exercise. We
recommend using binaries instead if those are available for your platform
via one of the above methods.
For details on how to build from source, see
[the building from source guide in the SciPy docs][building-docs].

[building-docs]: https://scipy.github.io/devdocs/building/index.html

'''

{{</ tabs >}}

See next steps in the [SciPy user guide](https://docs.scipy.org/doc/scipy/tutorial/).

<0></0>

## Installing with Type Stubs

Los archivos de tipado están disponibles a través de un paquete separado, "scipy-stubs", en PyPI y conda-forge.
También puede instalar SciPy y `scipy-stubs` como un solo paquete, a través del paquete adicional `scipy-stubs[scipy]` en PyPI, o el paquete `scipy-typed` en conda-forge.
Para obtener una versión específica `x.y.z` de SciPy (como `1.14.1`), debe instalar la versión `x.y.z.*`, por ejemplo:

```bash
uv add "scipy-stubs[scipy]==1.14.1.*" # or
pixi add "scipy-typed=1.15.0.*" # or
python -m pip install "scipy-stubs[scipy]" # or
conda install "scipy-typed>=1.14"
```

Dirija sus preguntas sobre la compatibilidad y soporte de tipado al [repositorio GitHub `scipy-stubs`] (https://github.com/jorenham/scipy-stubs).
