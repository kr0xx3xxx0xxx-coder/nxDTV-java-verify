# nxDTV_java BACKLOG

이 파일은 nxDTV_java 미해결 항목의 **단일 진실 공급원**이다.
완료보고 md 파일과 내용이 어긋나면 이 파일이 우선한다.

- 번호 체계: `JM-###` (Java Migration). nxDTV(Python)의 `M-` 번호와 구분한다.
- 상태 값: 미착수 / 보류 / 외부 의존 대기 / 선택사항 / 진행 중 / 완료

## 요약

| 번호 | 제목 | 상태 |
|---|---|---|
| JM-001 | JSON 라이브러리(Jackson) 도입 | 보류(현행 유지 확정) |
| JM-002 | Spring Boot 도입 재판단 | 보류 |
| JM-003 | 화면 프레임워크(Thymeleaf/Vaadin/React 등) 결정 | 외부 의존 대기 |
| JM-004 | DBMS 선택 UI 추가 | 미착수 |
| JM-005 | gradlew run 태스크 부재 | 미착수 |
| JM-006 | ParseHandler/Json.java 단위테스트 부재 | 미착수 |
| JM-007 | Playwright firefox/webkit 자동설치로 용량 1.2GB | 선택사항 |

---

## JM-001: JSON 라이브러리(Jackson) 도입

- **상태**: 보류(현행 유지 확정)
- **등록일**: 2026-09-16
- **내용**: ParseHandler의 JSON 직렬화를 Jackson으로 바꿀지 검토했으나,
  build.gradle의 "런타임 예외는 JSQLParser 하나뿐" 원칙과 충돌해 보류.
  수작업 Json.java 유지.
- **재논의 조건**: 화면이 커져 JSON 처리가 실제 부담이 될 때.

## JM-002: Spring Boot 도입 재판단

- **상태**: 보류
- **등록일**: 2026-09-16
- **내용**: P0에서 "웹서버 없음→불필요" 판단, 현재 최소 UI(JDK HttpServer)로
  유지 중.
- **재논의 조건**: 실 DB 연동(PreValidator/StatsValidator) 단계 진입 시.

## JM-003: 화면 프레임워크(Thymeleaf/Vaadin/React 등) 결정

- **상태**: 외부 의존 대기
- **등록일**: 2026-09-16
- **내용**: xDataNexPro 소개서 기준 8개 프로그램이 공유 레이아웃 관례(왼쪽 메뉴
  등)를 따르나 Plug-in 방식이라 프레임워크 공유 의무는 없어 보임. 다만
  nxTDA(Spring Boot) 쪽 결정과 맞출지 확인 필요.
- **재논의 조건**: nxTDA 담당 세션과 소통 가능해질 때.

## JM-004: DBMS 선택 UI 추가

- **상태**: 미착수
- **등록일**: 2026-09-16
- **내용**: 현재 화면은 SQL 하나만 입력받아 dbms 미지정으로 처리(식별자 폴딩
  미적용). 백엔드는 이미 dbms 인자를 받음.
- **재논의 조건**: 다음 UI 단계 착수 시.

## JM-005: gradlew run 태스크 부재

- **상태**: 미착수
- **등록일**: 2026-09-16
- **내용**: build.gradle 수정 금지 조건 때문에 P6-UI-1에서 추가 안 함.
  현재는 java -cp로 수동 기동.
- **재논의 조건**: 개발 편의성이 실제로 문제될 때.

## JM-006: ParseHandler/Json.java 단위테스트 부재

- **상태**: 미착수
- **등록일**: 2026-09-16
- **내용**: P6-UI-1은 실제 HTTP/브라우저 경로로만 검증, JUnit 테스트는 없음.
- **재논의 조건**: 웹 계층이 더 커지기 전(Claude Code 자체 권고).

## JM-007: Playwright firefox/webkit 자동설치로 용량 1.2GB

- **상태**: 선택사항
- **등록일**: 2026-09-16
- **내용**: PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD 적용하면 chromium만 남길 수 있음.
- **재논의 조건**: 디스크 공간이 실제로 문제될 때.
