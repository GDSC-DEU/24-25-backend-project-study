# Node.js - NestJS 프로젝트 설정

## Node 설치
Node.js는 JavaScript 런타임으로, JavaScript를 실행할 수 있는 환경을 제공합니다. NestJS는 Node.js 위에서 동작하는 프레임워크이므로, 먼저 Node.js를 설치해야 합니다.

Node.js 설치를 위해서 [Node.js 프로젝트 기초 설정](../../project_configuration_fundamental/node.md) 문서를 참고하여 Node.js를 설치해 주세요.

## NestJS 프로젝트 생성
NestJS는 Node.js 위에서 동작하는 프레임워크로, 효율적이고 확장 가능한 서버 사이드 애플리케이션을 개발할 수 있게 해줍니다. NestJS 프로젝트는 Nest CLI를 사용하여 쉽게 생성할 수 있습니다.

### Nest CLI 설치
1. Nest CLI를 설치하기 위해, 터미널에서 다음 명령어를 입력합니다:
   ```bash
   npm install -g @nestjs/cli
   ```
2. 설치가 완료되면, 다음 명령어로 Nest CLI가 올바르게 설치되었는지 확인합니다:
   ```bash
    nest --version
    ```
    Nest CLI의 버전 정보가 출력되면 성공입니다. 만약 `nest` 명령어를 찾을 수 없다고 나오면, 재설치를 진행해야 합니다.

### NestJS 프로젝트 생성

1. Nest CLI를 사용하여 NestJS 프로젝트를 생성합니다. 다음 명령어를 입력합니다:
    ```bash
    nest new backend_study
    ```
    프로젝트 이름은 원하는 대로 변경할 수 있습니다.
2. 프로젝트 생성 과정에서 패키지 매니저를 선택하라는 메시지가 나타납니다. `npm` 또는 `yarn` 중 원하는 것을 선택합니다. 여기서는 `npm`을 선택하겠습니다.
    만일 원하시는 패키지 매니저가 있다면, 따로 선택하셔도 괜찮습니다!
3. 프로젝트가 생성되면, 생성된 디렉토리로 이동후 다음 명령어로 NestJS 애플리케이션을 실행합니다:
    ```bash
    cd backend_study
    npm run start
    ```
    만약 프로젝트명을 `backend_study`가 아닌 다른 이름으로 생성했다면, 해당 디렉토리로 이동해 주세요.
4. 이제 Postman에서 `http://localhost:3000/` 주소로 GET 요청을 보내면, 다음과 같은 JSON 응답을 받을 수 있습니다:
    ```txt
    hello world!
    ```

축하합니다! 이제 NestJS 프로젝트가 성공적으로 생성되었고, 기본적인 애플리케이션이 실행되었습니다. 이 프로젝트를 기반으로 더 복잡한 기능을 추가해 나갈 수 있습니다.
