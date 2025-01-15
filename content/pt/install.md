---
title: Instalação
sidebar: false
---

Os métodos de instalação incluem:

- [Distribuições](#distributions)
- [pip](#pip-install)
- [conda](#pip-install)
- [Gerenciador de Pacotes](#package_manager)
- [Código fonte](#source)

Os métodos diferem na facilidade de uso, cobertura, manutenção das versões antigas, e no uso e controle local ou em todo o sistema. Com pip ou
conda (da Anaconda), você pode controlar as versões do pacote de um projeto
específico para evitar conflitos. O conda também controla pacotes que não são do Python,
como MKL ou HDF5. Gerenciadores de pacotes de sistema, como `apt-get`, instalam pacotes em todo o seu sistema, muitas vezes em versões mais antigas e oferecem menos versões disponíveis. A compilação a partir do código fonte é muito mais difícil
mas é necessária para depuração de problemas e desenvolvimento. Se você não sabe qual método
de instalação você precisa ou prefere, recomendamos a Distribuição [Anaconda](https://www.anaconda.com/download/) de Python Científico.

<a name="distributions"></a>

# Distribuições de Python Científico (recomendado)

Distribuições de Python fornecem o interpretador para a linguagem Python, junto com os pacotes e ferramentas mais utilizados. Esses arquivos, que podem ser obtidos através de download direto, demandam configuração mínima, funcionam em quase qualquer sistema, e fornecem quase todas as ferramentas necessárias para o Python científico.

A distribuição [Anaconda](https://www.anaconda.com/download/) funciona no Windows, Mac,
e Linux, fornece mais de 1.500 pacotes Python e é usada por mais de 15
milhões de pessoas. A Anaconda é mais adequada para os usuários iniciantes; ela fornece
uma grande coleção de bibliotecas de uma só vez.

Para usuários mais avançados que precisarão instalar ou atualizar regularmente,
[Mambaforge](https://github.com/conda-forge/miniforge#mambaforge) é uma maneira mais
adequada para instalar o `conda` (e `mamba`, um `conda` alternativo mais rápido).

Outras opções incluem:

- [WinPython](https://winpython.github.io): Outra distribuição livre
  incluindo pacotes científicos e a IDE Spyder; Apenas para Windows, mas
  com mais atualizações de manutenção e suporte às últimas versões do Python 3.
- [Pyzo](https://pyzo.org): Uma distribuição gratuita baseada na Anaconda
  e no ambiente de desenvolvimento interativo IEP; Suporta Linux,
  Windows e Mac.

<a name="pip-install"></a>

# Instalando com Pip

Você pode instalar a SciPy a partir do PyPI com `pip`:

```
python -m pip install scipy
```

<a name="conda-install"></a>

# Instalando via Conda

Você pode instalar a SciPy a partir dos canais `defaults` ou `conda-forge` com `conda`:

```
conda install scipy
```

<a name="package_manager"></a>

# Install system-wide via a package manager

System package managers can install the most common Python packages.
They install packages for the entire computer, often use older versions,
and don't have as many available versions.

## Ubuntu and Debian

Using `apt-get`:

```
sudo apt-get install python3-scipy
```

## Fedora

Using `dnf`:

```
sudo dnf install python3-scipy
```

## macOS

macOS doesn't have a preinstalled package manager, but you can install
[Homebrew](https://brew.sh/) and use it to install SciPy (and Python itself):

```
brew install scipy
```

<a name="source"></a>

# Source packages

A word of warning: building SciPy from source can be a nontrivial exercise. We
recommend using binaries instead if those are available for your platform.
For details on how to build from source, see
[this guide in the SciPy docs](https://scipy.github.io/devdocs/building/index.html).
