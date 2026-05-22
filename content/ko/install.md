---
title: 설치
sidebar: false
---

{{< admonition tip >}}
이 페이지는 터미널 사용이 익숙하고 패키지 관리자 사용법을 익히는 데 거부감이
없으시다는 것을 전제로 합니다. 초보자이시고 가능한 한 빠르게 SciPy를 시작하고 싶으시다면,
[초보자용 설치 안내](./beginner-install.md)를 확인해 주십시오!
{{< /admonition >}}

SciPy를 설치하는 권장 방식은 선호하시는 작업 흐름에 따라 달라집니다.
일반적인 작업 흐름은 대체로 다음과 같이 분류할 수
있습니다:

- **프로젝트 기반 방식** (예: `uv`, `pixi`) _(새 사용자에게 권장)_
- **환경 기반 방식** (예: `pip`, `conda`) _(전통적인 작업 흐름)_
- **시스템 패키지 관리자** _(권장하지 않음)_
- **소스에서 빌드하기** _(디버깅 및 개발용)_

SciPy를 \[정적 타입 스텁]과 함께 설치하시려면,
[타입 스텁과 함께 설치하기](#type-stubs)를 참고해 주십시오.

[static type stubs]: https://typing.readthedocs.io/en/latest/guides/libraries.html

{{< admonition tip >}}
통합 개발 환경(IDE)이 정확한 타입 힌트를 제공하려면
타입 스텁의 설치가 필요할 수 있습니다.
{{< /admonition >}}

{{< tabs >}}

[[tab]]
name = '프로젝트 기반'
content = ''' <a name="project-based"></a>

### uv로 설치하기

아래는 파이썬 패키지 관리자인 uv를 사용하여 SciPy를 사용할 프로젝트를 설정하는 단계별 가이드입니다.

1. [uv 문서의 안내](https://docs.astral.sh/uv/getting-started/installation/)에 따라 `uv`를 설치하십시오.

2. 터미널에서 다음을 실행하여, 새 하위 디렉터리에 새 프로젝트를 만드십시오:

```bash
uv init try-scipy
cd try-scipy
```

{{< admonition hint >}}
두 번째 명령은 해당 프로젝트의 디렉터리로 이동시킵니다.
{{< /admonition >}}

3. 프로젝트에 SciPy를 추가하기:

```bash
uv add scipy
```

{{< admonition note >}}
파이썬이 아직 설치되어 있지 않다면 자동으로 함께 설치됩니다!
{{< /admonition >}}

{{< admonition tip >}}
다른 파이썬 라이브러리도 같은 방식으로 설치하실 수 있습니다. 예를 들어

```bash
uv add matplotlib
```

{{< /admonition >}}

4. SciPy를 사용해 보세요!

```bash
uv run python
```

위 명령은 파이썬 인터프리터 세션을 실행하며, 거기서 `import scipy`를 사용하실 수 있습니다.

<!-- prettier-ignore-end -->

다음 단계는 [SciPy 사용자 가이드][scipy-user-guide]를 참고해 주십시오.

[scipy-user-guide]: https://docs.scipy.org/doc/scipy/tutorial/

{{< admonition note >}}

컴퓨터를 재부팅한 후에는, `try-scipy` 프로젝트 디렉터리로 이동하여
`uv run python`을 실행하면 SciPy가 import 가능한 파이썬 인터프리터로
돌아갈 수 있습니다.
파이썬 스크립트를 실행하려면 `uv run myscript.py`를 사용하실 수 있습니다.

자세한 내용은 [uv의 프로젝트 작업 가이드][uv-projects]를 참고해 주십시오.

[uv-projects]: https://docs.astral.sh/uv/guides/projects/

{{< /admonition >}}

### `pixi`로 설치하기

파이썬 외의 패키지를 함께 다루신다면, SciPy를 [Conda] 패키지로
설치하시는 편을 선호하실 수 있습니다. 그러면 파이썬 패키지 색인인
[PyPI](https://pypi.org/)에서 제공하지 않는 패키지들에 대해서도 동일한 작업 흐름을
사용하실 수 있기 때문입니다.
Conda는 어떤 언어의 패키지든 관리할 수 있으므로, 파이썬 자체나
컴파일러, 그 외 다른 언어를 설치하는 데도 사용하실 수 있습니다.

[Conda]: https://docs.conda.io/projects/conda/en/latest/index.html

패키지 관리 도구 [`pixi`]를 사용하여 [conda-forge]에서 SciPy를 설치하는 단계는
`uv`와 매우 유사합니다:

[conda-forge]: https://conda-forge.org/
[`pixi`]: https://pixi.sh/latest/

1. [`pixi` 문서의 안내][install-pixi]에 따라 `pixi`를 설치하십시오.

[install-pixi]: https://pixi.sh/latest/

2. 새 하위 디렉터리에 새 프로젝트를 만드십시오:

```bash
pixi init try-scipy
cd try-scipy
```

3. 프로젝트에 SciPy를 추가하기:

```bash
pixi add scipy
```

4. SciPy를 사용해 보세요!

```bash
pixi run python
```

'''

[[tab]]
name = '환경 기반'
content = ''' <a name="environment-based"></a>

프로젝트 기반 작업 흐름에서, 프로젝트란 프로젝트를 설명하는 매니페스트 파일,
프로젝트의 정확한 의존성을 기록하는 잠금(lock) 파일, 그리고 프로젝트의
(여러 개일 수도 있는) 환경을 포함하는 디렉터리를 가리킵니다.

이와 달리,
환경 기반 작업 흐름에서는 환경에 패키지를 설치하고,
그 환경을 어느 디렉터리에서나 활성화하거나 비활성화할 수 있습니다.
이러한 작업 흐름은 잘 정착되어 있지만,
프로젝트 기반 작업 흐름이 제공하는 재현성 이점은 일부 부족합니다.

### `pip`으로 설치하기

<!-- prettier-ignore-start -->

1. [파이썬을 설치하십시오](https://www.python.org/downloads/).

2. `venv`로 가상 환경을 만들고 활성화하십시오.

{{< admonition hint >}}
[Python Packaging User Guide의 튜토리얼](https://packaging.python.org/en/latest/tutorials/installing-packages/#creating-virtual-environments)을 참고해 주십시오.
{{< /admonition >}}

3. [`pip`]을 사용하여 SciPy를 설치하십시오:

```bash
python -m pip install scipy
```

<!-- prettier-ignore-end -->

[`pip`]: https://pip.pypa.io/en/stable/getting-started/

### `conda`로 설치하기

[Miniforge]는 Conda 기반 환경 관리자인 `conda`와 [`mamba`]를 설치하는
권장 방식입니다.
환경을 만든 후, 다음과 같이 conda-forge에서 SciPy를 설치하실 수 있습니다:

```bash
conda install scipy # or
mamba install scipy
```

[Miniforge]: https://conda-forge.org/download/
[`mamba`]: https://mamba.readthedocs.io/en/latest/

'''

[[tab]]
name = '패키지 관리자'
content = ''' <a name="system-package-managers"></a>

## 시스템 패키지 관리자를 사용하여 시스템 전역에 설치하기

시스템 패키지 관리자는 가장 일반적인 파이썬 패키지들을 설치할 수 있습니다.
시스템 패키지 관리자는 패키지를 컴퓨터 전체에 대해 설치하며, 보통 더 오래된 버전을
사용하고, 사용할 수 있는 버전 수도 그리 많지 않습니다. 권장하는 설치
방식은 아닙니다.

### Ubuntu와 Debian

`apt-get` 사용:

```bash
sudo apt-get install python3-scipy
```

### Fedora

`dnf` 사용:

```bash
sudo dnf install python3-scipy
```

### macOS

macOS에는 미리 설치된 패키지 관리자가 없지만,
[Homebrew](https://brew.sh/)를 설치하여 SciPy (와 파이썬 자체)를 설치하실 수 있습니다:

```bash
brew install scipy
```

'''

[[tab]]
name='Building from Source'
content = ''' <a name="building-from-source"></a>

미리 알려드리자면, SciPy를 소스에서 빌드하는 일은 간단하지 않을 수 있습니다. 사용하시는
플랫폼용 바이너리가 위의 방식 중 하나로 제공된다면, 바이너리 사용을
권장합니다.
소스에서 빌드하는 방법에 대한 자세한 사항은
[SciPy 문서의 소스 빌드 안내][building-docs]를 참고해 주십시오.

[building-docs]: https://scipy.github.io/devdocs/building/index.html

'''

{{</ tabs >}}

다음 단계는 [SciPy 사용자 가이드](https://docs.scipy.org/doc/scipy/tutorial/)를 참고해 주십시오.

<a name="type-stubs"></a>

## 타입 스텁과 함께 설치하기

정적 타입 스텁은 별도의 패키지인 `scipy-stubs`로, PyPI와 conda-forge에서
제공됩니다.
SciPy와 `scipy-stubs`를 하나의 패키지로 함께 설치하실 수도 있습니다.
PyPI에서는 `scipy-stubs[scipy]` 엑스트라를, conda-forge에서는
`scipy-typed` 패키지를 이용하시면 됩니다.
특정 버전 `x.y.z`의 SciPy (예: `1.14.1`)를 받으시려면,
`x.y.z.*` 버전을 설치하시면 됩니다. 예를 들어:

```bash
uv add "scipy-stubs[scipy]==1.14.1.*" # or
pixi add "scipy-typed=1.15.0.*" # or
python -m pip install "scipy-stubs[scipy]" # or
conda install "scipy-typed>=1.14"
```

정적 타입 지원에 대한 문의는
[`scipy-stubs` GitHub 저장소](https://github.com/jorenham/scipy-stubs)로 보내 주십시오.
