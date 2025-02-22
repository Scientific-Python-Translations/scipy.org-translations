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

<a name="project-based"></a>

## Flujos de trabajo basados en proyectos

### Instalando con `uv`

Aquí hay una guía paso a paso para configurar un proyecto para usar SciPy, con [`uv`], un administrador de paquetes de Python.

[`uv`]: https://docs.astral.sh/uv/

<!-- prettier-ignore-start -->

1. Instale `uv`, siguiendo [las instrucciones en la documentación de `uv`][install-uv].

[install-uv]: https://docs.astral.sh/uv/getting-started/installation/

2. Cree un nuevo proyecto en un nuevo subdirectorio, ejecutando el siguiente comando en una terminal:

   ```
   uv init try-scipy
   cd try-scipy
   ```

   {{< admonition hint >}}
   El segundo comando cambia el directorio al directorio de su proyecto.
   Si te acomoda usar una terminal y te interesa aprender
   a utilizar un gestor de paquetes, ¡échale un vistazo a
   [la guía principal de instalación](./install.md)!

3. Añada SciPy a tu proyecto:

   ```
   uv add scipy
   ```

   {{< admonition note >}}
   ¡Esto instalará Python automáticamente si aún no lo tiene instalado!
   Si te acomoda usar una terminal y te interesa aprender
   a utilizar un gestor de paquetes, ¡échale un vistazo a
   [la guía principal de instalación](./install.md)!

   {{< admonition tip >}}
   Puede instalar otras librerías de Python de la misma manera, por ejemplo

   uv add matplotlib

   Si te acomoda usar una terminal y te interesa aprender
   a utilizar un gestor de paquetes, ¡échale un vistazo a
   [la guía principal de instalación](./install.md)!

4. ¡Pruebe SciPy!

   ```
   uv run python
   ```

   This will launch a Python interpreter session, from which you can `import scipy`.

<!-- prettier-ignore-end -->

See next steps in [the SciPy user guide][scipy-user-guide].

[scipy-user-guide]: <>

{{< admonition note >}}

After rebooting your computer, you'll want to navigate to your `try-scipy`
project directory and execute `uv run python` to drop back into a Python interpreter
with SciPy importable.
To execute a Python script, you can use `uv run myscript.py`.

Read more at [the uv guide to working on projects][uv-projects].

[uv-projects]: https://docs.astral.sh/uv/guides/projects/

Si te acomoda usar una terminal y te interesa aprender
a utilizar un gestor de paquetes, ¡échale un vistazo a
[la guía principal de instalación](./install.md)!

### Installing with `pixi`

If you work with non-Python packages, you may prefer to install SciPy as
a [Conda] package, so that you can use the same workflow for packages which
are not available on [PyPI](https://pypi.org/), the Python Package Index.
Conda can manage packages in any language, so you can use it to install
Python itself, compilers, and other languages.

[Conda]: https://docs.conda.io/projects/conda/en/latest/index.html

The steps to install SciPy from [conda-forge] using the package management
tool [`pixi`] are very similar to the steps for `uv`:

[conda-forge]: https://conda-forge.org/
[`pixi`]: https://pixi.sh/latest/

1. Install `pixi`, following [the instructions in the `pixi` documentation][install-pixi].

[install-pixi]: https://pixi.sh/latest/

2. Create a new project in a new subdirectory:

   ```
   pixi init try-scipy
   cd try-scipy
   ```

3. Añada SciPy a tu proyecto:

   ```
   pixi add scipy
   ```

4. ¡Pruebe SciPy!

   ```
   pixi run python
   ```

See next steps in [the SciPy user guide][scipy-user-guide].

<a name="environment-based"></a>

## Environment-based workflows

In project-based workflows, a project is a directory containing a manifest
file describing the project, a lock-file describing the exact dependencies
of the project, and the project's (potentially multiple) environments.

In contrast,
in environment-based workflows you install packages into an environment,
which you can activate and deactivate from any directory.
These workflows are well-established,
but lack some reproducibility benefits of project-based workflows.

### Instalando con `pip`

<!-- prettier-ignore-start -->

1. [Install Python](https://www.python.org/downloads/).

2. Create and activate a virtual environment with `venv`.

   {{< admonition hint >}}
   See [the tutorial in the Python Packaging User Guide](https://packaging.python.org/en/latest/tutorials/installing-packages/#creating-virtual-environments).
   Si te acomoda usar una terminal y te interesa aprender
   a utilizar un gestor de paquetes, ¡échale un vistazo a
   [la guía principal de instalación](./install.md)!

3. Instala SciPy, utilizando [`pip`]:

   ```
   python -m pip install scipy
   ```

<!-- prettier-ignore-end -->

[`pip`]: https://pip.pypa.io/es/stable/getting-started/

### Instalando con `conda`

[Miniforge] es la forma recomendada de instalar `conda` y [`mamba`], dos administradores de entorno basados ​​en Conda.
Después de crear un entorno, puede instalar SciPy desde conda-forge de la siguiente manera:

```
conda install scipy # or
mamba install scipy
```

[Miniforge]: https://conda-forge.org/download/
[`mamba`]: https://mamba.readthedocs.io/es/latest/

<a name="system-package-managers"></a>

## Instalación en todo el sistema a través de un administrador de paquetes del sistema

Los administradores de paquetes del sistema pueden instalar los paquetes de Python más comunes.
Instalan paquetes para toda la computadora, a menudo usan versiones anteriores y no tienen tantas versiones disponibles. No son el método de instalación recomendado.

### Ubuntu y Debian

Usando `apt-get`:

```
sudo apt-get install python3-scipy
```

### Fedora

Usando `dnf`:

```
sudo dnf install python3-scipy
```

### macOS

macOS no tiene un administrador de paquetes preinstalado, pero puedes instalar [Homebrew](https://brew.sh/) y usarlo para instalar SciPy (y el propio Python):

```
brew install scipy
```

<0></0>

## Compilando desde el código fuente

Una advertencia: compilar SciPy desde el código fuente puede ser un ejercicio no trivial. Recomendamos utilizar binarios para su plataforma si están disponibles a través de uno de los métodos anteriores.
Para obtener detalles sobre cómo compilar desde el código fuente, consulte [la guía de compilación desde el código fuente en los documentos de SciPy][building-docs].

[building-docs]: https://scipy.github.io/devdocs/building/index.html

<0></0>

## Instalación con archivos de tipado

Los archivos de tipado están disponibles a través de un paquete separado, "scipy-stubs", en PyPI y conda-forge.
También puede instalar SciPy y `scipy-stubs` como un solo paquete, a través del paquete adicional `scipy-stubs[scipy]` en PyPI, o el paquete `scipy-typed` en conda-forge.
Para obtener una versión específica `x.y.z` de SciPy (como `1.14.1`), debe instalar la versión `x.y.z.*`, por ejemplo:

```
uv add "scipy-stubs[scipy]==1.14.1.*" # or
pixi add "scipy-typed=1.15.0.*" # or
python -m pip install "scipy-stubs[scipy]" # or
conda install "scipy-typed>=1.14"
```

Dirija sus preguntas sobre la compatibilidad y soporte de tipado al [repositorio GitHub `scipy-stubs`] (https://github.com/jorenham/scipy-stubs).
