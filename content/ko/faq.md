---
title: 자주 묻는 질문 (FAQ)
sidebar: false
---

## SciPy란 무엇입니까?

SciPy는 파이썬을 위한 오픈 소스(BSD 라이선스) 과학·수치 계산 도구들의
묶음입니다. 현재 특수 함수, 적분, 상미분 방정식(ODE) 솔버, 그래디언트 최적화,
병렬 프로그래밍 도구, 빠른 실행을 위한 표현식-C++ 컴파일러 등을
지원합니다. 대략적인 기준을 말씀드리자면, 수치 계산에 관한 일반 교재(예: 잘 알려진
Numerical Recipes 시리즈)에서 다루어지는 내용은 SciPy에 구현되어 있을
가능성이 높습니다.

## 비용은 얼마입니까?

SciPy는 무료로 제공됩니다. 오픈 소스 소프트웨어로 배포되므로, 소스 코드에 완전히 접근할 수 있으며
관대한 BSD 라이선스가 허용하는 어떠한 방식으로도 사용하실 수 있습니다.

## SciPy의 라이선스 조건은 무엇입니까?

SciPy의 라이선스는 [여기](https://github.com/scipy/scipy/blob/main/LICENSE.txt)의
BSD 라이선스 조건에 따라, 상업적·비상업적 용도 모두에 대해
무료로 사용 가능합니다.

## 파이썬과 같은 인터프리터 언어로 작성된 SciPy가 어떻게 빠를 수 있습니까?

사실, 시간이 중요한 반복문은 보통 C, C++, 또는
Fortran으로 구현되어 있습니다. SciPy의 일부는 <https://www.netlib.org/>에서 자유롭게 제공되는
과학 계산 루틴 위에 얇은 코드 계층을 얹은 것입니다. Netlib은
C와 Fortran으로 작성된, 매우 가치 있고 견고한 과학 계산 알고리즘들의
방대한 저장소입니다. 이런 알고리즘을 다시 작성하는 것은 비현실적이고,
디버깅에만도 수년이 걸릴 수 있습니다. SciPy는 이러한 알고리즘을 파이썬에서 사용할 수 있도록
그 주위를 감싸는 "래퍼(wrapper)"를 생성하기 위한
여러 가지 방법을 사용합니다. 일부 래퍼는 C로 직접 손으로 작성하여 만들었으며, 나머지는 SWIG 또는
[f2py](https://numpy.org/doc/stable/f2py/index.html)를 사용하여 생성했습니다. SciPy에 더 최근에 추가된 기여 중 일부는 전적으로 또는 래퍼 형태로
[Cython](https://cython.org/)이나 [Pythran](https://pythran.readthedocs.io)을 사용해 작성되었습니다.

두 번째 답은, 어려운 문제에 대해서는 더 나은 알고리즘이 문제 해결에 걸리는
시간에 엄청난 차이를 만들 수 있다는 점입니다.
따라서, SciPy의 내장 알고리즘을 사용하시는 편이 단순한 알고리즘을 C로 직접 구현한 것보다
훨씬 빠를 수 있습니다.

## 버그를 발견했습니다. 어떻게 해야 합니까?

SciPy 개발팀은 SciPy를 가능한 한 안정적으로 만들기 위해 노력하고 있지만,
어떤 소프트웨어 제품에서나 그러하듯 버그는 발생합니다. 여러분의 소프트웨어에 영향을 주는 버그를 발견하셨다면,
[SciPy 버그 트래커](https://github.com/scipy/scipy/issues)에 티켓을 등록하여
알려 주십시오.

## SciPy에 어떻게 참여할 수 있습니까?

[커뮤니티](/community) 페이지로 이동해 주십시오.
코드, 테스트, 문서 작성과 웹사이트 관련 일에 도움을 주실
분들을 적극적으로 찾고 있습니다.

## 상용 지원도 받을 수 있습니까?

예, SciPy에 대한 상용 지원은 여러 회사에서 제공하고 있습니다.
예를 들면 [Anaconda](https://www.anaconda.com),
[Enthought](https://www.enthought.com),
[Quansight](https://www.quansight.com) 등입니다.

# NumPy vs. SciPy vs. 기타 패키지

## NumPy와 SciPy의 차이점은 무엇입니까?

이상적인 세계라면, NumPy는 배열 자료형과 가장 기본적인 연산
(인덱싱, 정렬, 형상 변경, 기본 원소별 함수 등)만 담고 있을 것입니다. 모든 수치 계산 코드는 SciPy에 있어야 합니다.
하지만 NumPy의 중요한 목표 중 하나가 호환성이기 때문에, NumPy는
전신 라이브러리들에서 지원하던 기능들을 모두 유지하려 합니다.
따라서 NumPy에는 선형 대수 함수와 푸리에 변환 등이 일부 포함되어 있는데,
사실 이러한 기능은 SciPy에 더 적합합니다. 어쨌든
SciPy에는 선형 대수 모듈의 더 완전한 구현과, 그 외에도 많은 수치 계산
알고리즘이 포함되어 있습니다. 파이썬으로 과학 계산을 하신다면
NumPy와 SciPy를 모두 설치하시는 편이 좋습니다. 대부분의 새 기능은 NumPy보다는 SciPy에 추가됩니다.

## SciPy로 어떻게 플롯을 그릴 수 있습니까?

플롯 그리기 기능은 SciPy의 범위 밖에 있습니다. SciPy는
수치 객체와 알고리즘에 집중합니다. 엄청나게 인기 있는
[Matplotlib](https://matplotlib.org)처럼,
SciPy와 긴밀하게 통합되어 고품질 플롯을 만들어 주는 여러 패키지가 있습니다. 그 외
인기 있는 선택지로는 [Bokeh](https://bokeh.pydata.org/en/latest),
[Plotly](https://plot.ly), [Altair](https://altair-viz.github.io) 등이 있습니다.

## SciPy로 어떻게 3D 플롯/시각화를 만들 수 있습니까?

2D 플롯과 마찬가지로, 3D 그래픽도 SciPy의 범위 밖에 있지만,
2D의 경우처럼 SciPy와 통합되는 패키지들이 있습니다.
[Matplotlib](https://matplotlib.org)은 `mplot3d` 하위 패키지에서 기본적인 3D 플롯 기능을
제공하며,
[Mayavi](https://docs.enthought.com/mayavi/mayavi/)는 강력한
[VTK](https://www.vtk.org/) 엔진을 활용하여
다양한 고품질 3D 시각화 기능을 제공합니다.

## 왜 `numpy.linalg`과 `scipy.linalg` 두 가지가 모두 있습니까? 차이점은 무엇입니까?

`scipy.linalg`은
[f2py](https://numpy.org/doc/stable/f2py/index.html)를 사용한
Fortran [LAPACK](https://www.netlib.org/lapack/)의 보다 완전한 래퍼입니다.

NumPy의 설계 목표 중 하나는 Fortran 컴파일러 없이도 빌드할 수 있게 하는 것이었으므로,
LAPACK을 사용할 수 없는 환경에서는
NumPy가 자체 구현을 사용합니다. SciPy는 빌드를 위해 Fortran 컴파일러가 필요하며,
래핑된 Fortran 코드에 크게 의존합니다.

NumPy와 SciPy의 `linalg` 모듈에는
일부 공통 함수가 있지만 docstring이 서로 다르고,
`scipy.linalg`에는 `numpy.linalg`에 없는 함수들이
포함되어 있습니다. 예를 들어 LU
분해,
슈어
분해 관련 함수,
여러 가지 의사역행렬 계산 방식, 그리고 행렬
로그 같은
행렬 초월 함수 등입니다. 양쪽 모두에 존재하는 일부 함수는 `scipy.linalg`에서 기능이 더
확장되어 있습니다. 예를 들어 `scipy.linalg.eig`은
일반화 고유값
문제를 풀기 위해
두 번째 행렬 인자를 받을 수 있습니다.

# 파이썬 버전 지원

## NumPy와 SciPy는 여전히 Python 2.7을 지원합니까?

Python 2.7을 지원하는 NumPy의 마지막 버전은 NumPy 1.16.x입니다. 동일한 SciPy의
마지막 버전은 SciPy 1.2.x입니다. Python 3.x를 지원하는 NumPy의 첫
배포 버전은 NumPy 1.5.0이었습니다. SciPy에서 Python 3 지원은 SciPy 0.9.0에서
시작되었습니다.

## SciPy는 PyPy와 함께 동작합니까?

일반적으로는 그렇습니다. 최근 [PyPy](https://pypy.org)의 개선 덕분에
과학 파이썬 스택이 PyPy에서 동작하게 되었습니다. SciPy의 많은 부분이 C
확장 모듈로 구현되어 있기 때문에, 코드 실행 속도가 더 빨라지지 않을 수 있으며
(대부분의 경우 여전히 상당히 느리지만, PyPy는 이를 개선하기 위해
적극적으로 작업하고 있습니다). 벤치마킹할 때 늘 그렇듯,
직접 경험해 보시는 것이 가장 좋은 길잡이입니다.

## SciPy는 Jython이나 C#/.NET과 함께 동작합니까?

아니요, 어느 쪽도 지원되지 않습니다. Jython은 자바 가상 머신 위에서 실행되며,
표준 파이썬(CPython) 인터프리터용으로 C로 작성된 확장과 인터페이스할 방법이 없기 때문에
동작한 적이 없습니다.

몇 년 전에는, NumPy와 SciPy를 .NET과 호환되게 만들려는
시도가 있었습니다. 당시 일부 사용자는 32비트
Windows에서 [Ironclad](https://code.google.com/archive/p/ironclad)와 함께
NumPy를 사용하는 데 성공했다고 보고했습니다. 마지막으로, [Pyjion](https://pyjion.readthedocs.io/)은 새로운 프로젝트로,
SciPy와 함께 동작할 수 있다고 알려져 있습니다.

어쨌든 이러한 런타임/컴파일러는 SciPy의 범위 밖에 있으며, 개발팀에서
공식적으로 지원하지 않습니다.

# 도움을 받을 수 있는 곳

[커뮤니티](/community) 페이지를 참고해 주십시오.
