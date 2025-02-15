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
- [Compilando a partir do código-fonte](#building-from-source) (para depuração e desenvolvimento)

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

### Instalando com `pixi`

Se você trabalha com pacotes que não sejam Python puro, você pode preferir instalar o pacote SciPy com o [Conda], para que você possa usar o mesmo fluxo de trabalho para pacotes que
não estão disponíveis no [PyPI](https://pypi.org/), o Python Package Index.
Conda pode gerenciar pacotes em qualquer linguagem, então você pode usá-lo para instalar o próprio Python, compiladores e outras linguagens.

[Conda]: https://docs.conda.io/projects/conda/en/latest/index.html

Os passos para instalar SciPy a partir do [conda-forge] usando a ferramenta
de gerenciamento de pacotes [`pixi`] são muito semelhantes aos passos para o `uv`:

[conda-forge]: https://conda-forge.org/
[`pixi`]: https://pixi.sh/latest/

1. Instale o `pixi`, seguindo [as instruções na documentação do `pixi`][install-pixi].

[install-pixi]: https://pixi.sh/latest/

2. Crie um novo projeto em um novo subdiretório:

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

## Fluxos de trabalho baseados em ambientes

Em fluxos de trabalho baseados em projetos, um projeto é um diretório que contém um arquivo manifesto descrevendo o projeto, um arquivo <i>lock-file</i> descrevendo as dependências exatas do projeto, e os (potencialmente vários) ambientes do projeto.

Em contrapartida, em fluxos de trabalho baseados em ambientes você instala pacotes em um ambiente, que você pode ativar e desativar de qualquer diretório.
Estes fluxos de trabalho são bem estabelecidos, mas não possuem alguns benefícios de fluxos de trabalho baseados em projetos.

### Instalando com `pip`

<!-- prettier-ignore-start -->

1. [Instale o Python](https://www.python.org/downloads/).

2. Crie e ative um ambiente virtual com o `venv`.

   {{< admonition hint >}}
   Veja [o tutorial no Python Packaging User Guide](https://packaging.python.org/en/latest/tutorials/installing-packages/#creating-virtual-environments).
   {{< /admonition >}}

3. Instale a SciPy, usando [`pip`]:

   ```
   python -m pip install scipy
   ```

<!-- prettier-ignore-end -->

[`pip`]: https://pip.pypa.io/en/stable/getting-started/

### Instalando com `conda`

O [miniforge] é a ferramenta recomendada para instalar o `conda` e o [`mamba`],
dois gerenciadores de ambientes virtuais baseados em Conda.
Depois de criar um ambiente, você pode instalar a SciPy a partir do conda-forge da seguinte forma:

```
conda install scipy # ou
mamba install scipy
```

[Miniforge]: https://conda-forge.org/download/
[`mamba`]: https://mamba.readthedocs.io/en/latest/

<a name="system-package-managers"></a>

## Instalar todo o sistema por meio de um gerenciador de pacotes do sistema

Os gerenciadores de pacotes do sistema operacional podem instalar os pacotes Python mais comuns.
Eles instalam pacotes para o computador inteiro, muitas vezes usam versões mais antigas,
e não têm tantas versões disponíveis. Esse não é o método recomendado de instalação.

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

## Compilar a partir do código-fonte

Cuidado: compilar a SciPy a partir do código fonte pode ser um exercício não trivial. Recomendamos o uso de binários, em vez disso, se eles estiverem disponíveis para a sua plataforma em um dos métodos acima.
Para mais detalhes sobre como compilar a partir do código fonte, consulte
\[o guia de compilação a partir do código fonte na documentação da SciPy[building-docs].

[building-docs]: https://scipy.github.io/devdocs/building/index.html

<a name="type-stubs"></a>

## Instalando com os stubs de tipagem

Os stubs de tipagem estática estão disponíveis através de um pacote separado, `scipy-stubs`, no PyPI e conda-forge.
Você também pode instalar a SciPy e `scipy-stubs` como um único pacote,
através do pacote `scipy-stubs[scipy]` no PyPI, ou do pacote `scipy-typed`
no conda-forge.
Para obter uma versão específica do arquivo 'x.y.z' da SciPy (como '1.14.1'),
você deve instalar a versão 'x.y.z.\*', por exemplo:

```
uv add "scipy-stubs[scipy]==1.14.1.*" # or
pixi add "scipy-typed=1.15.0.*" # or
python -m pip install "scipy-stubs[scipy]" # or
conda install "scipy-typed>=1.14"
```

Por favor, envie questões diretas sobre suporte à tipagem estática para
[o repositório do `scipy-stubs` no GitHub](https://github.com/jorenham/scipy-stubs).
