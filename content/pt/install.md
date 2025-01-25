---
title: Instalação
sidebar: false
---

{{< admonition tip >}}
Esta página pressupõe que você se sente confortável usando um terminal e se dispõe a aprender como usar um gerenciador de pacotes. Se você é um iniciante e só quer iniciar o
com SciPy o mais rápido possível, confira o
[guia de instalação para iniciantes](./beginner-install.md)!
{{< /admonition >}}

O método recomendado para instalar a SciPy depende do seu fluxo de trabalho preferido.
Os fluxos de trabalho comuns podem ser divididos nas seguintes categorias:

- [Fluxo de trabalho baseado em projetos (p. ex: `uv`, `pixi`)](#project-based) (recomendado para novos usuários)
- Fluxo de trabalho baseado no ambiente (por exemplo, `pip`, `conda`)](#environment-based) (o fluxo de trabalho tradicional)
- [Gerenciador de pacotes do sistema](#system-package-managers) (não recomendado)
- [Compilando a partir do código fonte](#building-from-source) (para depuração e desenvolvimento)

Para instalar a SciPy com \[stubs para tipagem estática],
veja [Instalando com stubs para tipagem](#type-stubs).

[static type stubs]: https://typing.readthedocs.io/en/latest/guides/libraries.html

<a name="project-based"></a>

## Fluxos de trabalho baseados em projeto

### Instalando com `uv`

Aqui está um guia passo-a-passo para criar um projeto para usar a SciPy, com [`uv`],
um gerenciador de pacotes Python.

[`uv`]: https://docs.astral.sh/uv/

<!-- prettier-ignore-start -->

1. Instale `uv`, seguindo [as instruções na documentação do `uv`][install-uv].

[install-uv]: https://docs.astral.sh/uv/getting-started/installation/

2. Criar um novo projeto em um novo subdiretório, executando o seguinte em um terminal:

   ```
   uv init try-scipy
   cd try-scipy
   ```

   {{< admonition hint >}}
   O segundo comando muda o diretório para dentro do diretório do seu projeto.
   {{< /admonition >}}

3. Adicione SciPy ao seu projeto:

   ```
   uv add scipy
   ```

   {{< admonition note >}}
   Isto irá instalar o Python automaticamente se você ainda não o tiver instalado!
   {{< /admonition >}}

   {{< admonition tip >}}
   Você pode instalar outras bibliotecas de Python da mesma forma, por exemplo

   uv add matplotlib

   {{< /admonition >}}

4. Experimente a SciPy!

   ```
   uv run python
   ```

   Isto irá lançar uma sessão do interpretador do Python, a partir da qual você pode fazer `import scipy`.

<!-- prettier-ignore-end -->

Para as próximas etapas, consulte [o guia do usuário SciPy][scipy-user-guide].

[scipy-user-guide]: https://docs.scipy.org/doc/scipy/tutorial/

{{< admonition note >}}

Depois de reiniciar o computador, você deve navegar até o diretório do seu projeto `try-scipy`
e executar `uv run python` para entrar novamente em uma sessão do interpretador Python
com a SciPy disponível para ser importada.
Para executar um script Python, você pode usar `uv run myscript.py`.

Leia mais no [guia uv para trabalhar em projetos][uv-projects].

[uv-projects]: https://docs.astral.sh/uv/guides/projects/

{{< /admonition >}}

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

3. Adicione SciPy ao seu projeto:

   ```
   pixi add scipy
   ```

4. Experimente a SciPy!

   ```
   pixi run python
   ```

Para as próximas etapas, consulte [o guia do usuário SciPy][scipy-user-guide].

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

### Installing with `pip`

<!-- prettier-ignore-start -->

1. [Install Python](https://www.python.org/downloads/).

2. Create and activate a virtual environment with `venv`.

   {{< admonition hint >}}
   See [the tutorial in the Python Packaging User Guide](https://packaging.python.org/en/latest/tutorials/installing-packages/#creating-virtual-environments).
   {{< /admonition >}}

3. Install SciPy, using [`pip`]:

   ```
   python -m pip install scipy
   ```

<!-- prettier-ignore-end -->

[`pip`]: https://pip.pypa.io/en/stable/getting-started/

### Installing with `conda`

[Miniforge] is the recommended way to install `conda` and [`mamba`],
two Conda-based environment managers.
After creating an environment, you can install SciPy from conda-forge as follows:

```
conda install scipy # or
mamba install scipy
```

[Miniforge]: https://conda-forge.org/download/
[`mamba`]: https://mamba.readthedocs.io/en/latest/

<a name="system-package-managers"></a>

## Installing system-wide via a system package manager

Os gerenciadores de pacotes do sistema operacional podem instalar os pacotes Python mais comuns.
Eles instalam pacotes para o computador inteiro, muitas vezes usam versões mais antigas,
e não têm tantas versões disponíveis. They are not the recommended
installation method.

### Ubuntu e Debian

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

macOS não tem um gerenciador de pacotes pré-instalado, mas você pode instalar o
[Homebrew](https://brew.sh/) e usá-lo para instalar a SciPy (e o Python em si):

```
brew install scipy
```

<a name="building-from-source"></a>

## Building from source

Cuidado: compilar a SciPy a partir do código fonte pode ser um exercício não trivial. We
recommend using binaries instead if those are available for your platform
via one of the above methods.
For details on how to build from source, see
[the building from source guide in the SciPy docs][building-docs].

[building-docs]: https://scipy.github.io/devdocs/building/index.html

<a name="type-stubs"></a>

## Installing with type stubs

Static type stubs are available via a separate package, `scipy-stubs`, on
PyPI and conda-forge.
You can also install SciPy and `scipy-stubs` as a single package,
via the `scipy-stubs[scipy]` extra on PyPI, or the `scipy-typed`
package on conda-forge.
To get a specific version `x.y.z` of SciPy (such as `1.14.1`),
you should install version `x.y.z.*`, for example:

```
uv add "scipy-stubs[scipy]==1.14.1.*" # or
pixi add "scipy-typed=1.15.0.*" # or
python -m pip install "scipy-stubs[scipy]" # or
conda install "scipy-typed>=1.14"
```

Please direct questions about static typing support to
[the `scipy-stubs` GitHub repository](https://github.com/jorenham/scipy-stubs).
