# Java/Kotlin 기초 설정

## 1. Java/Kotlin 설치
Java/Kotlin은 JVM(Java Virtual Machine) 위에서 실행되는 프로그래밍 언어입니다. 정상적인 실행을 위해서는 JDK(Java Development Kit)이 설치되어 있어야 합니다.

### Windows
#### 1. Winget을 이용한 설치
1. Windows에서 Winget이 설치되어 있다면, 다음 명령어를 입력하여 JDK를 설치할 수 있습니다:
   ```bash
   winget install -e --id Amazon.Corretto.21.JDK
   ```
   위 명령어는 Amazon Corretto 21 JDK를 설치합니다.
   - JDK 버전은 원하시는 버전을 선택할 수 있으나, 보통 8, 11, 21 버전이 많이 사용됩니다. 특히, JVM은 21버전부터 Virtual Threads를 지원하며 높은 성능 향상을 제공하기 때문에, 가능하면 21 버전을 추천합니다.
   - Amazon Corretto는 Amazon에서 제공하는 무료 오픈 소스 JDK 배포판입니다. 다른 버전들을 사용해도 괜찮으며, OpenJDK, Azul Zulu, Oracle JDK 등 다양한 배포판이 있습니다.
1. 설치가 완료되면, 다음 명령어로 설치된 JDK 버전을 확인합니다:
   ```bash
   java -version
   ```
    정상적으로 설치되었다면, JDK 버전 정보가 출력됩니다.

#### 2. 수동 설치
1. [Amazon Corretto JDK 다운로드 페이지](https://docs.aws.amazon.com/corretto/latest/corretto-21-ug/downloads-list.html)로 이동합니다.
1. Windows 운영체제에 맞는 JDK 설치 파일을 다운로드합니다.
1. 다운로드한 설치 파일을 실행하여 JDK를 설치합니다.
1. 설치가 완료되면, 다음 명령어로 설치된 JDK 버전을 확인합니다:
   ```bash
   java -version
   ```
   정상적으로 설치되었다면, JDK 버전 정보가 출력됩니다.


### MacOS
#### 1. Homebrew를 이용한 설치
1. MacOS에서 Homebrew가 설치되어 있다면, 다음 명령어를 입력하여 JDK를 설치할 수 있습니다:
   ```bash
   brew install --cask amazon-corretto21
   ```
   위 명령어는 Amazon Corretto 21 JDK를 설치합니다.
   - JDK 버전은 원하시는 버전을 선택할 수 있으나, 보통 8, 11, 21 버전이 많이 사용됩니다. 특히, JVM은 21버전부터 Virtual Threads를 지원하며 높은 성능 향상을 제공하기 때문에, 가능하면 21 버전을 추천합니다.
   - Amazon Corretto는 Amazon에서 제공하는 무료 오픈 소스 JDK 배포판입니다. 다른 버전들을 사용해도 괜찮으며, OpenJDK, Azul Zulu, Oracle JDK 등 다양한 배포판이 있습니다.
1. 설치가 완료되면, 다음 명령어로 설치된 JDK 버전을 확인합니다:
    ```bash
    java -version
    ```
    정상적으로 설치되었다면, JDK 버전 정보가 출력됩니다.

#### 2. 수동 설치
1. [Amazon Corretto JDK 다운로드 페이지](https://docs.aws.amazon.com/corretto/latest/corretto-21-ug/downloads-list.html)로 이동합니다.
2. MacOS 운영체제에 맞는 JDK 설치 파일을 다운로드합니다.
3. 다운로드한 설치 파일을 실행하여 JDK를 설치합니다.
4. 설치가 완료되면, 다음 명령어로 설치된 JDK 버전을 확인합니다:
   ```bash
   java -version
   ```
   정상적으로 설치되었다면, JDK 버전 정보가 출력됩니다.

## 2. Gradle 설치
Gradle은 Java/Kotlin 프로젝트의 빌드 도구로, 의존성 관리 및 빌드 프로세스를 자동화하는 데 사용됩니다.
Gradle 이전에는 Ant, Maven 등의 빌드 도구가 사용되었으나, Gradle이 설정에서 조금 더 유연하고 쉽게 사용할 수 있기 때문에, 이번 스터디에서는 Gradle을 사용하도록 하겠습니다.

!! tip: Spring boot 프로젝트를 생성할 때, Gradle의 경우 Wrapper를 지원하기 때문에, 이 설치 과정은 선택 사항이 됩니다. 다만, Gradle을 직접 설치해두면, 다른 Java/Kotlin 프로젝트에서도 유용하게 사용할 수 있습니다.
### Windows
출처: [Gradle 공식 문서 - Windows 설치](https://docs.gradle.org/current/userguide/installation.html#windows_installation)

1. [Gradle 다운로드 페이지](https://gradle.org/releases/)로 이동하여, 최신 버전의 Gradle을 다운로드합니다.
    - 이 때, Binary-only와 full distribution 중에서 binary-only를 다운로드합니다. full distribution은 문서, 소스 코드를 포함하고 있어, 용량이 더 크지만, 일반적으로 binary-only로 충분합니다.
2. 다운로드한 ZIP 파일을 C:\gradle 디렉토리에 압축 해제합니다.
3. 시스템 환경 변수에 Gradle을 추가합니다:
   - `내 PC`를 우클릭하고 `속성`을 선택합니다.
   - `고급 시스템 설정`을 클릭합니다.
   - `환경 변수` 버튼을 클릭합니다.
   - `시스템 변수`에서 `Path` 변수를 찾아 편집합니다.
   - 새 항목으로 C:\gradle\bin을 추가합니다.
   혹은, 검색에서 "환경 변수"를 검색하여, 시스템 환경 변수 설정 창으로 이동할 수 있습니다.
4. 명령 프롬프트를 열고 다음 명령어로 Gradle이 정상적으로 설치되었는지 확인합니다:
    ```bash
    gradle -v
    ```
    정상적으로 설치되었다면, Gradle 버전 정보, JVM 정보 등이 아래와 같이 출력됩니다.
    ```
    Welcome to Gradle 8.14.1!

    Here are the highlights of this release:
     - Java 24 support
     - GraalVM Native Image toolchain selection
     - Enhancements to test reporting
     - Build Authoring improvements

    For more details see https://docs.gradle.org/8.14.1/release-notes.html


    ------------------------------------------------------------
    Gradle 8.14.1
    ------------------------------------------------------------

    Build time:    2025-05-22 13:44:09 UTC
    Revision:      c174b82566a79e3575bac8c7648c7b36cd815e94

    Kotlin:        2.0.21
    Groovy:        3.0.24
    Ant:           Apache Ant(TM) version 1.10.15 compiled on August 25 2024
    Launcher JVM:  21.0.7 (Amazon.com Inc. 21.0.7+6-LTS)
    Daemon JVM:    C:\Program Files\Amazon Corretto\jdk21.0.7_6 (no JDK specified, using current Java home)
    OS:            Windows 11 10.0 amd64
    ```

### MacOS
출처: [Gradle 공식 문서 - MacOS 설치](https://docs.gradle.org/current/userguide/installation.html#macos_installation)
#### 1. SDKMan을 이용한 설치(권장)
SDKMan은 다양한 JVM 기반의 도구들을 관리할 수 있는 유틸리티로, Gradle 설치 및 버전 관리를 쉽게 할 수 있습니다.
1. 터미널을 열고 다음 명령어를 입력하여 SDKMan을 설치합니다:
   ```bash
   curl -s "https://get.sdkman.io" | bash
   ```
2. 설치가 완료되면, 터미널을 재시작하거나 다음 명령어를 입력하여 SDKMan을 활성화합니다:
    ```bash
    source "$HOME/.sdkman/bin/sdkman-init.sh"
    ```
3. 다음 명령어로 Gradle을 설치합니다:
    ```bash
    sdk install gradle
    ```
4. 설치가 완료되면, 다음 명령어로 Gradle이 정상적으로 설치되었는지 확인합니다:
    ```bash
    gradle -v
    ```
    정상적으로 설치되었다면, Gradle 버전 정보, JVM 정보 등이 출력됩니다.

