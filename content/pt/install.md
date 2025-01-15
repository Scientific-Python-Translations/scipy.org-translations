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

# Instalação via Pip

Você pode instalar a SciPy a partir do PyPI com `pip`:

```
python -m pip install scipy
```

<a name="conda-install"></a>

# Instalação via Conda

Você pode instalar a SciPy a partir dos canais `defaults` ou `conda-forge` com `conda`:

```
conda install scipy
```

<a name="package_manager"></a>

# Instalação via gerenciador de pacotes

Os gerenciadores de pacotes do sistema operacional podem instalar os pacotes Python mais comuns.
Eles instalam pacotes para o computador inteiro, muitas vezes usam versões mais antigas,
e não têm tantas versões disponíveis.

## Ubuntu e Debian

Usando `apt-get`:

```
sudo apt-get install python3-scipy
```

## Fedora

Usando `dnf`:

```
sudo dnf install python3-scipy
```

## macOS

macOS não tem um gerenciador de pacotes pré-instalado, mas você pode instalar o
[Homebrew](https://brew.sh/) e usá-lo para instalar a SciPy (e o Python em si):

```
brew install scipy
```

<a name="source"></a>

# Pacotes gerados a partir do código fonte

Cuidado: compilar a SciPy a partir do código fonte pode ser um exercício não trivial. Recomendamos o uso de binários, em vez disso, se eles estiverem disponíveis para a sua plataforma.
Para obter detalhes sobre como compilar a biblioteca a partir do código fonte, consulte
[este guia na documentação da SciPy](https://scipy.github.io/devdocs/building/index.html).
