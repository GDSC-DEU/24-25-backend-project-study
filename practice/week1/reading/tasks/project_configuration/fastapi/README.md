## Python - FastAPI 프로젝트 설정

시작하기 전, 반드시 Python 기본 설치를 완료해 주세요. [Python 기본 설치](../../project_configuration_fundamental/python.md)

## FastAPI 설치
FastAPI는 Python으로 작성된 현대적인 웹 프레임워크로, 빠르고 효율적인 API 개발을 지원합니다. FastAPI를 설치하기 위해서는 먼저 Python이 설치되어 있어야 합니다. Python과 pipenv이 설치되어 있지 않다면, [Python 설치](../../project_configuration_fundamental/python.md) 단계를 따라 설치해 주세요.

1. 프로젝트 폴더에서, 다음과 같은 명령어를 입력하여 FastAPI와 Uvicorn을 설치합니다:
   ```bash
   pipenv install fastapi uvicorn
   ```

2. 설치가 완료되면, 다음 명령어로 FastAPI와 Uvicorn이 올바르게 설치되었는지 확인합니다:
   ```bash
    pipenv run uvicorn --version
    ```

Uvicorn의 버전 정보가 출력되면 성공입니다. 만약 `uvicorn` 명령어를 찾을 수 없다고 나오면, 재설치를 진행해야 합니다.

## FastAPI 프로젝트 구조 설정
FastAPI 프로젝트를 시작하기 전에, 기본적인 프로젝트 구조를 설정하는 것이 좋습니다. 다음과 같은 구조를 추천합니다:

```
backend_study/
├── app/               # FastAPI 애플리케이션 디렉토리
│   ├── main.py        # FastAPI 애플리케이션의 진입점
│   ├── settings.py    # 설정 파일
│   ├── database.py    # 데이터베이스 연결 설정
│   ├── routers/       # 라우터 디렉토리. /api로 해도 괜찮습니다.
│   ├── models/        # 데이터 모델 디렉토리. 데이터베이스 모델이나 Pydantic 모델을 포함합니다.
│   ├── services/      # 서비스 디렉토리. 비즈니스 로직을 포함합니다.
│   └── utils/         # 유틸리티 함수 디렉토리. 공통적으로 사용되는 함수들을 포함합니다.
├── tests/             # 테스트 디렉토리. 테스트 파일들을 포함합니다.
│   └── test_main.py
└── README.md
```

이 구조는 FastAPI 애플리케이션을 모듈화하고, 유지보수를 용이하게 합니다.
우선은, 프로그램이 실행되는지를 확인하기 위해, `app/main.py` 파일을 생성하고 다음과 같은 코드를 작성합니다:

```python
from fastapi import FastAPI
app = FastAPI()
@app.get("/")
def read_root():
    return {"Hello": "World"}
```

이제 FastAPI 애플리케이션을 실행해 보겠습니다. 터미널에서 다음 명령어를 입력합니다:

```bash
pipenv run uvicorn app.main:app --reload
```

이 명령어는 `app/main.py` 파일에서 FastAPI 애플리케이션을 찾아 실행합니다. `--reload` 옵션은 코드 변경 시 자동으로 서버를 재시작하게 해줍니다.

Postman에서 `http://localhost:8000/` 주소로 GET 요청을 보내면, 다음과 같은 JSON 응답을 받을 수 있습니다:

```json
{
    "Hello": "World"
}
```

수고하셨습니다! FastAPI 프로젝트 초기 설정이 완료되었습니다. 이제 이 구조를 기반으로 API를 개발해 나갈 수 있습니다. 추가적인 라우터, 모델, 서비스 등을 구현하여 기능을 확장해 나가면 됩니다.