# 프로젝트 설정 - Python 기본

## Python 설치

### 1. Windows
#### 1. Winget 사용(추천)
1. PowerShell을 관리자 권한으로 실행합니다.
2. 다음 명령어를 입력합니다(Python 3.13 버전을 설치합니다. 다른 버전을 설치하고 싶다면 뒤의 `3.13`을 원하는 버전으로 변경하세요):
   ```powershell
   winget install Python.Python.3.13
   ```
3. Python이 설치되엇는지 확인합니다:
   ```powershell
   python --version
   ```
   Python 버전이 출력되면 성공입니다. 만약 `python` 명령어를 찾을 수 없다고 나오면, 재설치를 진행해야 합니다.

#### 2. Chocolatey 사용
1. PowerShell을 관리자 권한으로 실행합니다.
2. Chocolatey가 설치되어 있지 않다면, 다음 명령어로 설치합니다:
   ```powershell
   Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
   ```
3. Python을 설치합니다:
   ```powershell
    choco install python -y
    ```
4. Python이 설치되엇는지 확인합니다:
    ```powershell
    python --version
    ```
    Python 버전이 출력되면 성공입니다. 만약 `python` 명령어를 찾을 수 없다고 나오면, 재설치를 진행해야 합니다.


#### 3. 설치 프로그램 사용
1. [Python 공식 웹사이트](https://www.python.org/downloads/)에서 Windows용 설치 프로그램을 다운로드합니다.
2. 다운로드한 설치 프로그램을 실행합니다.
3. 설치 옵션에서 "Add Python to PATH"를 선택합니다.
4. "Install Now"를 클릭하여 설치를 진행합니다.
5. 설치가 완료되면, 명령 프롬프트(CMD) 또는 PowerShell을 열고 다음 명령어를 입력하여 Python이 올바르게 설치되었는지 확인합니다:
   ```powershell
   python --version
   ```
   Python 버전이 출력되면 성공입니다. 만약 `python` 명령어를 찾을 수 없다고 나오면, 재설치를 진행해야 합니다.


### 2. MacOS
#### 1. Homebrew 사용(권장)
1. 터미널을 열고 Homebrew가 설치되어 있는지 확인합니다:
   ```bash
   brew --version
   ```
2. Homebrew가 설치되어 있지 않다면, 다음 명령어로 설치합니다:
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
3. Python을 설치합니다:
   ```bash
   brew install python
   ```
4. Python이 설치되었는지 확인합니다:
   ```bash
   python3 --version
   ```
   Python 버전이 출력되면 성공입니다. 만약 `python3` 명령어를 찾을 수 없다고 나오면, 재설치를 진행해야 합니다.

#### 2. 설치 프로그램 사용
1. [Python 공식 웹사이트](https://www.python.org/downloads/)에서 macOS용 설치 프로그램을 다운로드합니다.
2. 다운로드한 .pkg 파일을 실행합니다.
3. 설치 옵션에서 "Add Python to PATH"를 선택합니다.
4. 설치가 완료되면, 터미널을 열고 다음 명령어를 입력하여 Python이 올바르게 설치되었는지 확인합니다:
   ```bash
   python3 --version
   ```
   Python 버전이 출력되면 성공입니다. 만약 `python3` 명령어를 찾을 수 없다고 나오면, 재설치를 진행해야 합니다.



## 가상 환경 설정
Python을 시작하기 전에 가장 먼저 알아야 할 것은 **가상 환경**입니다. 가상 환경은 프로젝트마다 독립적인 Python 환경을 제공하여, 패키지 충돌을 방지하고 프로젝트 간의 의존성을 관리할 수 있게 해줍니다.

파이썬의 `pip`은 기본적으로 패키지를 시스템 전역에 설치합니다. 이는 여러 프로젝트가 존재할 때, 서로 충돌하거나 에러가 발생할 수 있다는 단점이 있습니다.
이를 해결하기 위해서 python 개발 커뮤니티에서는 다양한 가상 환경 관리 도구를 제공하고 있습니다:
- `venv`: Python 표준 라이브러리로 제공되는 가상 환경 관리 도구입니다.
- `virtualenv`: `venv`의 기능을 확장한 도구로, 더 많은 기능을 제공합니다.
- `pipenv`: `pip`과 `virtualenv`의 기능을 통합한 도구로, 의존성 관리와 가상 환경 관리를 동시에 제공합니다.
- `poetry`: Python 패키지 관리와 의존성 관리를 통합한 도구로, 현대적인 패키지 관리 기능을 제공합니다.

위 관리 도구 중에서, 이번에는 pipenv를 사용하여 가상 환경을 설정할 것입니다. pipenv는 기본적으로 사용하기 쉽고, 다른 언어(특히 node)와 유사한 패키지 관리 방식을 제공합니다. 따라서, 다른 언어를 사용해본 경험이 있다면 쉽게 사용할 수 있습니다.
만일 다른 패키지 관리 도구를 사용하고 싶으시다면, 스터디장에게 문의 후 스터디 진행에 사용하셔도 괜찮습니다!

### pipenv 설치
1. pipenv를 설치하기 위해, 먼저 Python이 설치되어 있어야 합니다. Python이 설치되어 있지 않다면, 위의 [Python 설치](#python-설치) 단계를 따라 설치합니다.
2. pipenv를 설치합니다. 터미널(또는 CMD, PowerShell)을 열고 다음 명령어를 입력합니다:
   ```bash
   pip install pipenv
   ```
3. pipenv가 설치되었는지 확인합니다. 다음 명령어를 입력하여 pipenv 버전을 확인합니다:
   ```bash
   pipenv --version
   ```

### 프로젝트 디렉토리 생성
1. 원하는 위치에 프로젝트 디렉토리를 생성합니다. 예를 들어, `backend_study`라는 이름의 디렉토리를 생성하려면 다음 명령어를 입력합니다:
   ```bash
   mkdir backend_study
   cd backend_study
   ```

### 가상 환경 생성
1. 프로젝트 디렉토리에서 다음 명령어를 입력하여 가상 환경을 생성합니다:
   ```bash
   pipenv --python 3.13
   ```
   여기서 `3.13`은 원하는 Python 버전으로 변경할 수 있습니다. 다만, 해당 버전이 시스템에 설치되어 있어야 합니다.

완료되었다면, 가상 환경이 생성되고, 해당 디렉토리에 `Pipfile`과 `Pipfile.lock` 파일이 생성됩니다. 이 파일들은 프로젝트의 의존성을 관리하는 데 사용됩니다.

이제 가상 환경이 준비되었습니다. 해당하는 기술스택 문서로 돌아가서, 다음 단계를 진행하시면 됩니다.
