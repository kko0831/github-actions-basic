# GitHub Actions 기본 예제

이 저장소는 GitHub Actions 워크플로의 기본 실행 방법을 확인하기 위한 예제입니다.

## 워크플로 동작

`.github/workflows/deploy.yml`에 정의된 워크플로는 `main` 브랜치에 코드가 push될 때 실행됩니다.

- 실행 환경: `ubuntu-latest`
- Job: `My-Deploy-Job`
  1. `Hello World 찍기`: `Hello World`를 출력
  2. `여러 명령어 문장 작성하기`: `|`를 사용해 여러 줄 명령어로 `Good`, `Morning`을 차례로 출력
  3. `Github Actions 자체에 저장되어 있는 변수 사용해보기`: GitHub Actions가 기본 제공하는 환경 변수 `GITHUB_SHA`(커밋 SHA), `GITHUB_REPOSITORY`(저장소 이름)를 출력
  4. `아무한테 노출이 되면 안 되는 값`: 저장소 Secrets에 등록한 `MY_NAME`, `MY_HOBBY` 값을 `${{ secrets.* }}`로 참조해 출력 (로그에는 `***`로 마스킹되어 표시)

현재 워크플로는 배포를 수행하지 않으며, 실행 여부를 확인하기 위한 간단한 예제입니다.

## 주요 개념

| 개념 | 설명 |
| --- | --- |
| Workflow | 자동화 작업의 전체 단위 (`name`으로 이름 지정) |
| Event (`on`) | 워크플로가 실행되는 시점 (여기서는 `main` 브랜치 push) |
| Job | 하나의 워크플로를 구성하는 작업 묶음. 기본적으로 병렬 실행 |
| Step | Job 안에서 특정 작업을 수행하는 가장 작은 단위 |
| `run: \|` | YAML 멀티라인 문법으로 여러 명령어를 한 Step에서 실행 |
| 기본 환경 변수 | 별도 설정 없이 사용할 수 있는 변수 (예: `$GITHUB_SHA`, `$GITHUB_REPOSITORY`) |
| Secrets | 노출되면 안 되는 값을 저장소 설정(**Settings > Secrets and variables > Actions**)에 등록하고 `${{ secrets.이름 }}`으로 참조. 로그에서는 마스킹됨 |

## 실행 결과 확인

1. 저장소 Secrets에 `MY_NAME`, `MY_HOBBY`를 등록합니다.
2. 변경 사항을 `main` 브랜치에 push합니다.
3. GitHub 저장소의 **Actions** 탭에서 `Github Actions 실행시켜보기` 워크플로 실행을 확인합니다.
4. 실행된 `My-Deploy-Job` 작업의 로그에서 `Hello World`, `Good`, `Morning`, 커밋 SHA와 저장소 이름 출력을 확인하고, Secrets 값은 `***`로 마스킹되어 보이는지 확인합니다.
