# 프로젝트 설정 - NodeJS 기본

## Node.js 설치
Node.js는 JavaScript 런타임으로, JavaScript를 실행할 수 있는 환경을 제공합니다.
Node는 메이저 버전(LTS)를 매년 4월에 출시하고 있습니다. 지원 기간이 긴 만큼, 가능하면 LTS 버전을 사용하는 것이 좋습니다.

혹시, 다양한 프로젝트에서 다른 Node 버전을 사용할 것으로 예상되는 경우, **nvm(Node Version Manager)**을 사용하여 Node.js 버전을 관리할 수 있습니다. nvm은 여러 버전의 Node.js를 설치하고 쉽게 전환할 수 있게 해줍니다.

이 프로젝트에서는 우선 일반적인 Node.js 설치 방법을 사용하겠습니다. 만약 이미 NVM을 사용하고 있다면, 아래 과정을 생략하고 NVM을 사용하여 Node.js를 설치하시면 됩니다.

### Windows
#### 1. WinGet 사용(권장)
1. Windows PowerShell을 관리자 권한으로 실행합니다.
1. 다음 명령어를 입력하여 Node.js를 설치합니다:
   ```powershell
   winget install OpenJS.NodeJS.LTS -s winget
   ```
1. 설치가 완료되면, 다음 명령어로 Node.js와 npm이 올바르게 설치되었는지 확인합니다:
    ```powershell
    node --version
    npm --version
    ```


#### 2. Node.js 공식 웹사이트에서 설치
1. [Node.js 공식 웹사이트](https://nodejs.org/)에 접속합니다.
1. LTS 버전을 다운로드합니다.
1. 다운로드한 설치 파일을 실행하고, 설치 과정에서 기본 설정을 그대로 유지합니다.
1. 설치가 완료되면, 다음 명령어로 Node.js와 npm이 올바르게 설치되었는지 확인합니다:
    ```powershell
    node --version
    npm --version
    ```


### macOS
#### 1. Homebrew 사용(권장)
1. 터미널을 열고, 다음 명령어를 입력하여 Homebrew가 설치되어 있는지 확인합니다:
   ```bash
   brew --version
   ```
   Homebrew가 설치되어 있지 않다면, [Homebrew 공식 웹사이트](https://brew.sh/)의 지침에 따라 설치합니다.

2. Homebrew를 사용하여 Node.js를 설치합니다:
   ```bash
   brew install node@lts
   ```

3. 설치가 완료되면, 다음 명령어로 Node.js와 npm이 올바르게 설치되었는지 확인합니다:
   ```bash
   node --version
   npm --version
   ```

#### 2. Node.js 공식 웹사이트에서 설치
1. [Node.js 공식 웹사이트](https://nodejs.org/)에 접속합니다.
2. LTS 버전을 다운로드합니다.
3. 다운로드한 설치 파일을 실행하고, 설치 과정에서 기본 설정을 그대로 유지합니다.
4. 설치가 완료되면, 다음 명령어로 Node.js와 npm이 올바르게 설치되었는지 확인합니다:
   ```bash
   node --version
   npm --version
   ```