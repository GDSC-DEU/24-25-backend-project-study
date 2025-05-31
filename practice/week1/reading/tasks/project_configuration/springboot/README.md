# Java/Kotlin - Spring boot 프로젝트 시작

이 문서는 Java/Kotlin 기반의 Spring Boot 프로젝트를 시작하기 위한 가이드를 제공합니다.

우선, Java/Kotlin 및 Gradle이 설치되어 있어야 합니다. 설치가 되어 있지 않다면, [Java/Kotlin 기초 설정](../../project_configuration_fundamental/java-kotlin.md) 문서를 참고하여 설치해 주세요.

## 1. Spring Boot 프로젝트 생성
Spring Boot 프로젝트는 [Spring Initializr](https://start.spring.io/)를 통해 쉽게 생성할 수 있습니다. 다음 단계를 따라 프로젝트를 생성해 주세요.

1. [Spring Initializr](https://start.spring.io/) 웹사이트로 이동합니다.
2. 다음과 같은 설정을 입력합니다:
   - Project: Gradle-Kotlin (Groovy DSL도 가능하나, 타입 세이프티와 최신 기능을 지원하는 Kotlin DSL을 추천합니다)
   - Language: Java 또는 Kotlin 중 선택
   - Spring Boot: 최신 버전 선택
   - Project Metadata:
       - Group: 아무거나 해도 됩니다. 모를 경우 학교 이름으로 합시다. 예: `com.gdsc.deu.backend`
       - Artifact: 시스템에서 인지할 프로젝트 이름 (예: `study-2425`)
       - Name: 사람이 인지할 프로젝트 이름 (예: `24-25 backend study`)
       - Description: 프로젝트 설명 (예: `Backend Study Project`)
       
    - Packageing: JAR 선택, WAR는 이미 실행중인 Web 서버에 배포할 때 사용되므로, 이번 스터디에서는 JAR로 진행합니다.
    - Java: 가능한 최신 버전 LTS 선택 (가능한 경우)
    - Package Name: 자동으로 생성되나, [패키지 명 네이밍 컨벤션](https://docs.oracle.com/javase/tutorial/java/package/namingpkgs.html)에 따라, -가 포함될 경우 전부 _로 변경해야 합니다. 예: `com.gdsc.deu.backend.2425-study` => `com.gdsc.deu.backend.2425_study`
3. Dependencies(의존성) 섹션에서 다음 의존성을 추가합니다:
    - Spring Web: REST API 개발을 위한 필수 의존성
    - Spring Boot DevTools: 개발 편의성을 위한 도구
    - Lombok: 코드 간결화를 위한 라이브러리 (Java 사용 시, Kotlin은 포함하지 않아도 괜찮습니다)
    - Spring boot Actuator: 애플리케이션 모니터링 및 관리 기능을 제공
    - Distributed Tracing: 로그 분산 추적을 위한 span, ID 등을 제공(선택 사항입니다.)
4. Generate 버튼을 클릭하여 프로젝트를 생성합니다.
5. 생성된 ZIP 파일을 다운로드하고, 원하는 디렉토리에 압축을 해제합니다.
6. IDE(예: IntelliJ IDEA)에서 프로젝트를 엽니다.
7. IDE에서 Gradle을 인식할 경우, 자동으로 의존성을 다운로드하고 프로젝트를 설정합니다. 만약 자동으로 설정되지 않는다면, Gradle을 수동으로 실행하여 의존성을 다운로드합니다:
   - IntelliJ IDEA에서는 Gradle 탭에서 `Refresh` 버튼을 클릭하거나, 터미널에서 다음 명령어를 실행합니다:
     ```bash
     ./gradlew build
     ```

## 2. 프로젝트 구조 이해
프로젝트가 생성되면, 다음과 같은 기본 구조를 갖게 됩니다:

```
root-project/
├── gradle/                                 (Gradle 관련 파일)
├── src/                                    (소스 코드 디렉토리)
│   ├── main/
│   │   ├── java/                           (혹은 kotlin/)
│   │   │   └── com.../                     (패키지 구조)
│   │   │       └── Application.java        (혹은 Application.kt. 메인 실행 파일)
│   │   └── resources/
│   │       └── application.properties      (설정 파일)
│   └── test/
│       ├── java/                           (혹은 kotlin/)
│       │   └── com.../                     (패키지 구조)
│       │       └── ApplicationTests.java   (혹은 ApplicationTests.kt. 테스트 파일)
│       └── resources/
├── build.gradle.kts                        (프로젝트 빌드 설정 파일)
├── settings.gradle.kts                     (프로젝트 설정 파일)
├── gradlew[.bat]                           (Gradle Wrapper 스크립트)
└── .git[attributes/ignore]```              (Git 설정 파일)
```

이 구조는 Spring Boot 애플리케이션을 모듈화하고, 유지보수를 용이하게 합니다. `src/main/java` 디렉토리에는 애플리케이션의 소스 코드가 위치하고, `src/main/resources` 디렉토리에는 설정 파일과 정적 리소스가 위치합니다. `src/test/java` 디렉토리에는 테스트 코드가 위치합니다.

## 3. 애플리케이션 실행
이제 애플리케이션을 실행해 보겠습니다. `Application.java` 또는 `Application.kt` 파일이 있는 폴더에, `controller` 폴더를 생성하고, 그 안에 `HelloController.java` 또는 `HelloController.kt` 파일을 생성합니다. 다음과 같은 코드를 작성합니다:

```java
package com.gdsc.deu.backend.study_2425.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;
@RestController
public class HelloController {
    @GetMapping("/")
    public String hello() {
        return "Hello, World!";
    }
}
```
```kotlin
package com.gdsc.deu.backend.study_2425.controller
import org.springframework.web.bind.annotation.GetMapping
import org.springframework.web.bind.annotation.RestController

@RestController
class HelloController {
    @GetMapping("/")
    fun hello(): String {
        return "Hello, World!"
    }
}
```

이제 애플리케이션을 실행해 보겠습니다. IDE에서 `Application.java` 또는 `Application.kt` 파일을 실행하거나, 터미널에서 다음 명령어를 입력합니다:

```bash
./gradlew bootRun
```

이 명령어는 Gradle을 사용하여 Spring Boot 애플리케이션을 실행합니다. 애플리케이션이 성공적으로 실행되면, Postman에서 `http://localhost:8080/` 주소로 GET 요청을 보내면, 다음과 같은 응답을 받을 수 있습니다:

```txt
Hello, World!
```

이제 Spring Boot 프로젝트가 성공적으로 설정되었으며, 기본적인 REST API를 구현할 수 있는 환경이 준비되었습니다. 추가적인 기능을 구현하거나, 데이터베이스와 연동하는 등의 작업을 진행할 수 있습니다.