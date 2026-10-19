# greet-ci

명령행 인수로 받은 이름에 인사하는 Python 프로그램입니다. 인수가 없으면 `world`를 사용합니다.

## 설치

Python 3.11 이상, Git, uv 0.8.14를 준비한 뒤 저장소 루트에서 실행합니다.

```sh
uv sync --locked
```

## 실행

```sh
uv run --locked python greet.py Hee
# Hello, Hee!
uv run --locked python greet.py
# Hello, world!
```

## 검사 및 빌드

```sh
uv run --locked pytest -q greet.py
uv run --locked black --check greet.py
uv run --locked flake8 greet.py
uv run --locked mypy greet.py
uv build
```

CI는 main 대상 push와 pull request에서 실행됩니다. Ubuntu·Windows와 Python 3.11·3.12의 네 테스트 작업, 품질 검사 작업, 패키지 빌드 작업으로 구성됩니다. 테스트와 품질 검사가 성공하면 배포 파일을 빌드하고 `greet-dist` artifact로 보관합니다.
