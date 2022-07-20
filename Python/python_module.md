> # 모듈

### 개요

- 모듈 : 합, 평균, 표준편차 등 자주 쓰는 기능을 하나의 파일로
- 패키지 : 다양한 파일을 하나의 폴더로
- 라이브러리 : 다양한 패키지를 하나의 묶음으로
- pip : 이것을 관리하는 관리자
- 가상환경 : 패키지의 활용 공간

### 모듈과 패키지

- 모듈
  - 특정 기능을 하는 코드를 파이썬 파일(.py) 단위로 작성한 것
- 패키지
  - 특정 기능과 관련된 여러 모듈의 집합
  - 패키지 안에는 또 다른 서브 패키지를 포함
- 모듈과 패키지 불러오기
  - 모듈 불러오기
    - `import` module
    - `from` module `import` var, function, Class
    - `from` module `import` * *( * : 전부 다 )*
  - 패키지 불러오기
    - `from` package `import` module
    - `from` package.module `import` var, function, Class

### 파이썬 표준 라이브러리

- 파이썬에 기본적으로 설치된 모듈과 내장 함수
  - 예시) `random.py`
- 파이썬 패키지 관리자(pip)
  - Python Package Index에 저장된 외부 패키지들을 설치하도록 도와주는 패키지 관리 시스템
- 파이썬 패키지 관리자(pip) 명령어
  - 패키지 설치
    - 최신/특정/최소 버전을 명시하여 설치 가능
    - 이미 설치되어 있는 경우 이미 설치되어 있음을 알리고 아무것도 하지 않음
    - `$ pip install SomePackage`
    - `$ pip install SomePackage==1.0.5`
    - `$ pip install 'SomePackage>=1.0.4’`
  - 패키지 삭제
    - pip는 패키지 업그레이드를 하는 경우 과거 버전을 자동으로 지워줌
    - `$ pip uninstall SomePackage`
  - 패키지 목록 및 특정 패키지 정보
    - `$ pip list`
    - `$ pip show SomePackage`
  - 패키지 관리하기
    - 아래의 명령어들을 통해 패키지 목록을 관리[1]하고 설치할 수 있음[2]
    - 일반적으로 패키지를 기록하는 파일의 이름은 requirements.txt로 정의함
    - `$ pip freeze > requirements.txt`
    - `$ pip install -r reuqirements.txt`

### 가상환경

- 파이썬 표준 라이브러리가 아닌 외부 패키지와 모듈을 사용하는 경우 모두 pip를 통해 설치를 해야함

- 복수의 프로젝트를 하는 경우 버전이 상이할 수 있음
  
  - 과거 외주 플젝 - django 버전 2.x
  - 신규 회사 플젝 - django 버전 3.x

- 이런 경우 가상환경을 만들어 플젝별로 독립적인 패키지 관리 가능

- 가상 환경을 만들고 관리하는데 사용되는 모듈(Python 버전 3.5부터)

- 특정 디렉토리에 가상 환경을 만들고, 고유한 파이썬 패키지 집합을 가질 수 있음
  
  - 특정 폴더에 가상 환경이(패키지 집합 폴더 등) 있고
  - 실행 환경(ex. -bash)에서 가상환경을 활성화 시켜
  - 해당 폴더에 있는 패키지를 관리/사용함

- 가상환경 생성
  
  - 가상환경을 생성하면, 해당 디렉토리에 별도의 파이썬 패키지가 설치됨
  - `$ python -m venv <폴더명>`

- 가상환경 활성화/비활성화
  
  - 아래의 명령어를 통해 가상환경을 활성화
  
  - <venv>는 가상환경을 포함하는 디렉토리의 경로
    
    | 플랫폼   | 셀               | 가상 환경을 활성화하는 명령                     |
    | ----- | --------------- | ----------------------------------- |
    | POSIX | bash/zsh        | $ source <venv>/bin/activate        |
    |       | fish            | $ source <venv>/bin/activate.fish   |
    |       | csh/tcsh        | $ source <venv>/bin/activate.csh    |
    |       | PowerShell Core | $ source <venv>/bin/Activate.ps1    |
    | 윈도우   | cmd.exe         | C:\> <venv>\Scripts\activate.bat    |
    |       | PowerShell      | PS C:\> <venv>\Scripts\Activate.ps1 |
  
  - 가상환경 비활성화는 `$ deactivate` 명령어를 사용

### 유용한 패키지와 모듈

### 사용자 모듈과 패키지

- 패키지
  
  - 패키지는 여러 모듈/하위 패키지로 구조화
    - 활용 예시 : package.module
  - 모든 폴더에는 `__init__.py`를 만들어 패키지로 인식
    - Python 3.3부터는 파일이 없어도 되지만, 하위 버전 호환 및 프레임워크 등에서의 동작을 위해 파일을 생성하는 것을 권장

- 패키지 만들기
  
  - 계산 기능이 들어간 calculator 패키지를 아래와 같이 구성
    - [`check.py](<http://check.py>)` 에서 calculator의 `tools.py`의 기능을 사용

- 모듈 만들기 - calculator
  
  - calculator/tools.py 에 add 함수와 minus 함수 작성

- 모듈 활용하기 - check
  
  - 모듈을 활용하기 위해서는 import 문을 통해 가져옴
