# we-adk-welfare

비플페이(beplepay)가 개발 중인 **복지혜택 관리 플랫폼** 백엔드입니다.  
첫 번째 업무 도메인: **경조사지원** (결혼·출산·장례 등 경조사 이벤트에 대한 복지 지원)

## 기술 스택

| 항목 | 내용 |
|------|------|
| 언어 | Java 21 |
| 프레임워크 | Spring Boot 4.1.0 (Jakarta EE 10) |
| 보안 | Spring Security 6.x / JWT |
| ORM | Spring Data JPA 3.x / Hibernate 6 |
| DB | PostgreSQL |
| 빌드 | Gradle 9.x (Kotlin DSL, 멀티모듈) |

## 모듈 구조

```
we-adk-welfare/
├── we-adk-welfare-common/   ← 공통 인프라 라이브러리 (exception, response, util)
├── we-adk-welfare-domain/   ← 공통 도메인 라이브러리 (Entity, Repository)
├── we-adk-welfare-user/     ← 사용자 API 실행 모듈 (port: 8080)
├── we-adk-welfare-admin/    ← 관리자 API 실행 모듈 (port: 8081, skeleton)
└── we-adk-welfare-batch/    ← 배치 실행 모듈 (port: 8082, skeleton)
```

**의존 관계:** `user / admin / batch` → `domain` → `common`

## 빌드 및 실행

```bash
./gradlew build                                 # 전체 빌드
./gradlew :we-adk-welfare-user:bootRun          # 사용자 API 실행
./gradlew :we-adk-welfare-admin:bootRun         # 관리자 API 실행
./gradlew test                                  # 전체 테스트
./gradlew clean build                           # 클린 빌드
```

> Windows: `.\gradlew` 또는 `gradlew.bat` 사용

## 개발 워크플로

```
/dev-interview → /dev-plan → /develop → /qa-test → /code-review → /git → /pack
```

Claude Code 하네스 설정은 별도 레포([we-adk-welfare-harness](https://github.com/beple-dev-1/we-adk-welfare-harness))에서 관리합니다.

## 관련 레포

| 레포 | 설명 |
|------|------|
| [we-adk-welfare](https://github.com/beple-dev-1/we-adk-welfare) | 백엔드 개발 소스 (이 레포) |
| [we-adk-welfare-harness](https://github.com/beple-dev-1/we-adk-welfare-harness) | Claude Code 하네스 설정 |
