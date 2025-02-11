---
title: インストール
sidebar: false
---

{{< admonition tip >}}
このページの説明では、パッケージマネージャーの使い方を学ぶために、ターミナルを使うことには慣れていることを前提としています。 もしあなたが初心者で、できるだけ早くSciPyを始めたい場合は、[初心者向けインストールガイド](./beginner-install.md)をチェックしてみて下さい！
{{< /admonition >}}

SciPyのインストール方法は、実施したいワークフローによって異なります。
一般的なワークフローは大まかに下記のカテゴリに分類できます。

- [プロジェクトベースのワークフロー (例: `uv`, `pixi`を利用)](#project-based) (こちらは新規ユーザ向けに推奨)
- [環境ベースのワークフロー(例: `pip`, `conda`を利用)](#environment-based) (従来のワークフロー)
- [システムパッケージマネージャーを利用](#system-package-managers) (非推奨)
- [ソースコードのビルド](#building-from-source) (デバッグと開発用)

\[静的型スタブ]を使用してSciPyをインストールしたい場合は、こちらの[静的方スタブを利用したインストール方法](#type-stubs)を参照してください。

[static type stubs]: https://typing.readthedocs.io/en/latest/guides/libraries.html

<a name="project-based"></a>

## プロジェクトベースのワークフロー

### `uv`でインストールする

ここではPythonのパッケージマネージャー[`uv`]を使用してSciPyを導入するための、各ステップ毎のガイドを紹介します。

[`uv`]: https://docs.astral.sh/uv/

<!-- prettier-ignore-start -->

1. [uv のドキュメント内のインストール手順][install-uv]に従って、`uv`をインストールしてください。

[install-uv]: https://docs.astral.sh/uv/getting-started/installation/

2. ターミナルで以下を実行して、新しいサブディレクトリに新しいプロジェクトを作成します。

   ```
   uv init try-scipy
   cd try-scipy
   ```

   {{< admonition hint >}}
   二つ目のコマンドは、あなたのプロジェクトのディレクトリに直接移動しています。
   {{< /admonition >}}

3. SciPyをプロジェクトに追加:

   ```
   uv add scipy
   ```

   {{< admonition note >}}
   Python がまだインストールされていない場合、この作業により自動的にPythonがインストールされます！
   {{< /admonition >}}

   {{< admonition tip >}}
   他のPythonライブラリも同じようにインストールできます。
   例:

   uv add matplotlib

   {{< /admonition >}}

4. SciPyを試してみましょう！！

   ```
   uv run python
   ```

   Pythonインタプリタのセッションを起動します。そうすると`import scipy`ができるようになります。

<!-- prettier-ignore-end -->

次のステップに関しては、 [SciPyユーザガイド][scipy-user-guide]を確認ください。

[scipy-user-guide]: https://docs.scipy.org/doc/scipy/tutorial/

{{< admonition note >}}

コンピュータを再起動した場合、設定が初期化されるので、再度 `try-scipy`プロジェクトのディレクトリに移動し、 `uv run python` を実行すると、SciPyがインポートできる状態のPython インタプリタを再度起動することができます。
あるPython スクリプトを実行するには、 `uv run myscript.py` コマンドを使用します。

より詳細はこちらの[uvを使ったプロジェクト管理][uv-projects]を確認下さい。

[uv-projects]: https://docs.astral.sh/uv/guides/projects/

{{< /admonition >}}

### `pixi`を使ってインストールする

もし、Python以外のパッケージを利用している場合は、SciPyを[Conda]パッケージとしてインストールすると便利です。これにより、PyPI（Python Package Index）で提供されていないパッケージも同じワークフローで管理できるようになります。
Condaは任意の言語でパッケージを管理できるため、
Python自体や、コンパイラ、その他の言語をインストールするのにも使用できます。

[Conda]: https://docs.conda.io/projects/conda/en/latest/index.html

パッケージ管理ツール[`pixi`]を使用して[conda-forge]からSciPyをインストールする手順は、`uv`を使った場合と非常に似ています。

[conda-forge]: https://conda-forge.org/
[`pixi`]: https://pixi.sh/latest/

1. Install `pixi`, following [the instructions in the `pixi` documentation][install-pixi].

[install-pixi]: https://pixi.sh/latest/

2. Create a new project in a new subdirectory:

   ```
   pixi init try-scipy
   cd try-scipy
   ```

3. SciPyをプロジェクトに追加:

   ```
   pixi add scipy
   ```

4. SciPyを試してみましょう！！

   ```
   pixi run python
   ```

次のステップに関しては、 [SciPyユーザガイド][scipy-user-guide]を確認ください。

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

System package managers can install the most common Python packages.
They install packages for the entire computer, often use older versions,
and don't have as many available versions. They are not the recommended
installation method.

### Ubuntu and Debian

Using `apt-get`:

```
sudo apt-get install python3-scipy
```

### Fedora

Using `dnf`:

```
sudo dnf install python3-scipy
```

### macOS

macOS doesn't have a preinstalled package manager, but you can install
[Homebrew](https://brew.sh/) and use it to install SciPy (and Python itself):

```
brew install scipy
```

<a name="building-from-source"></a>

## Building from source

A word of warning: building SciPy from source can be a nontrivial exercise. We
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
