---
title: 초보자용 설치 안내
sidebar: false
---

{{< admonition tip >}}
이 페이지는 초보자용 설치 안내입니다.
터미널 사용이 익숙하고 패키지 관리자 사용법을 익히는 데 거부감이 없으시다면,
[기본 설치 안내](./install.md)를 확인해 보십시오!
{{< /admonition >}}

- [JupyterLite](#jupyterlite)
- [과학 파이썬 배포판](#distributions)
- [`pip`으로 시스템 전역에 설치](#pip-global)

<a name="jupyterlite"></a>

## JupyterLite

사이파이를 한번 사용해 보시려면, 설치하실 필요조차 없습니다!
https://jupyter.org/try-jupyter/lab/ 에서 브라우저로 사이파이를 사용하실 수 있습니다 -
파이썬 노트북을 열고 노트북 "셀"에 `import scipy`를 입력한 뒤
실행 버튼을 누르시면 됩니다.

다음 단계는 [SciPy 사용자 가이드][scipy-user-guide]에서 확인하실 수 있습니다.

[scipy-user-guide]: https://docs.scipy.org/doc/scipy/tutorial/

<a name="distributions"></a>

## 과학 파이썬 배포판

파이썬 배포판은 언어 자체와 함께 가장 널리 사용되는
패키지와 도구를 제공합니다. 이 다운로드 파일들은 설정 작업이 거의 필요 없고, 대부분의 환경에서 동작하며,
가장 널리 쓰이는 과학 파이썬 도구들을 모두 포함하고 있습니다.
[Anaconda](https://www.anaconda.com/download/)는 Windows, Mac,
Linux 에서 모두 동작하며, 처음 사용하시는 분들께 가장 적합합니다.
다른 선택지로는 다음과 같은 것들이 있습니다:

- [WinPython](https://winpython.github.io): 과학용 패키지와 Spyder IDE 를
  포함한 또 다른 무료 배포판; Windows 전용입니다.
- [Pyzo](https://pyzo.org): Anaconda 와 IEP 대화형 개발 환경을
  기반으로 한 무료 배포판; Linux, Windows,
  Mac 을 지원합니다.

{{< admonition note >}}
Anaconda 는 개인, 대학, 그리고 직원 200명 미만의 회사에서 무료로 사용할 수
있습니다. 자세한 내용은 Anaconda 의 안내 블로그 글
["when is Anaconda free to use?"](https://www.anaconda.com/blog/update-on-anacondas-terms-of-service-for-academia-and-research) 를 참고해 주십시오.
{{< /admonition >}}

과학 파이썬 배포판을 설치하신 후의 다음 단계는,
[SciPy 사용자 가이드][scipy-user-guide]를 참고해 주십시오.

<a name="pip-global"></a>

## `pip`으로 시스템 전역에 설치

이미 파이썬이 설치되어 있다면, 터미널/셸에서 다음을 실행하여
`pip`으로 사이파이를 설치하실 수 있습니다:

```
python -m pip install scipy
```

{{< admonition warning >}}
튜토리얼이나 강의에서 위 방법을 권장하는 경우를 보실 수 있지만,
`pip`으로 사이파이를 설치하는 권장 방식은 가상 환경을 사용하는 것입니다 -
[`pip`으로 설치하기](./install.md#installing-with-pip)를 참고해 주십시오.
{{< /admonition >}}

{{< admonition note >}}
이 방법을 권장하지 않는 이유에 대해서는,
[Python Packaging User Guide 의 가상 환경 안내](https://packaging.python.org/en/latest/tutorials/installing-packages/#creating-virtual-environments)를 참고해 주십시오.
{{< /admonition >}}
