# GitHub Actions 기본 예제

이 저장소는 GitHub Actions 워크플로의 기본 실행 방법을 확인하기 위한 예제입니다.

## 워크플로 동작

`.github/workflows/deploy.yml`에 정의된 워크플로는 `main` 브랜치에 코드가 push될 때 실행됩니다.

- 실행 환경: `ubuntu-latest`
- 작업: `Hello World`를 출력

현재 워크플로는 배포를 수행하지 않으며, 실행 여부를 확인하기 위한 간단한 예제입니다.

## 실행 결과 확인

1. 변경 사항을 `main` 브랜치에 push합니다.
2. GitHub 저장소의 **Actions** 탭에서 `Github Actions 실행시켜보기` 워크플로 실행을 확인합니다.
3. 실행된 `My-Deploy-Job` 작업의 로그에서 `Hello World` 출력을 확인합니다.
