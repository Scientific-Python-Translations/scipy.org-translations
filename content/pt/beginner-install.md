---
title: Guia de instalação para iniciantes
sidebar: false
---

{{< admonition tip >}}
Este é o guia de instalação para iniciantes.
Se você está confortável com o uso de um terminal e se dispõe a aprender
como usar um gerenciador de pacotes, confira
[o guia principal de instalação](./install.md)!
{{< /admonition >}}

- [JupyterLite](#jupyterlite)
- [Distribuições Científicas de Python](#distributions)
- [Instalando globalmente com `pip`](#pip-global)

<a name="jupyterlite"></a>

## JupyterLite

Para experimentar a SciPy, você nem precisa instalá-la!
Você pode usar a SciPy no seu navegador em https://jupyter. rg/try-jupyter/lab/ -
apenas abra um notebook Python, em seguida, escreva `import scipy` em uma das células do notebook e clique em executar.

Para as próximas etapas, consulte [o guia do usuário SciPy][scipy-user-guide].

[scipy-user-guide]: https://docs.scipy.org/doc/scipy/tutorial/

<a name="distributions"></a>

## Distribuições Científicas de Python

Distribuições de Python fornecem o interpretador para a linguagem Python, junto com os pacotes e ferramentas mais utilizados. Esses arquivos, que podem ser obtidos através de download direto, demandam configuração mínima, funcionam em quase qualquer sistema, e fornecem quase todas as ferramentas necessárias para o Python científico.
[Anaconda](https://www.anaconda.com/download/) funciona no Windows, Mac,
e Linux, e é mais adequado para usuários iniciantes.
Outras opções incluem:

- [WinPython](https://winpython.github.io): Outra distribuição gratuita
  incluindo pacotes científicos e o ID do Spyder; Windows apenas.
- [Pyzo](https://pyzo.org): Uma distribuição gratuita baseada na Anaconda
  e no ambiente de desenvolvimento interativo IEP; Suporta Linux,
  Windows e Mac.

{{< admonition note >}}
Anaconda é gratuita para indivíduos, universidades e empresas com menos de
200 funcionários. For more detail, see Anaconda's helpful blog on
["when is Anaconda free to use?"](https://www.anaconda.com/blog/update-on-anacondas-terms-of-service-for-academia-and-research)
{{< /admonition >}}

After installing a scientific Python distribution,
see next steps in [the SciPy user guide][scipy-user-guide].

<a name="pip-global"></a>

## Installing globally with `pip`

If you already have Python installed, you can install SciPy
with `pip` by executing the following in a terminal/shell:

```
python -m pip install scipy
```

{{< admonition warning >}}
You may see this recommended in tutorials or classes, but the recommended
way to install SciPy with `pip` is to use a virtual environment -
see [Installing with `pip`](./install.md#installing-with-pip).
{{< /admonition >}}

{{< admonition note >}}
For more information on why this is not a recommended installation method,
read about [virtual environments in the Python Packaging User Guide](https://packaging.python.org/en/latest/tutorials/installing-packages/#creating-virtual-environments).
{{< /admonition >}}
