2026-03-26(목)

# 관리자 공지사항 페이지 작업 기록

## 작업 목표

- 프론트에서 잘못 진행된 비즈니스 공지 연결 작업을 원복한다.
- 백엔드 관리자 페이지에서 `/admin/notice`가 정상 동작하도록 만든다.
- 관리자 공지사항 목록 조회, 등록, 수정, 삭제까지 JSP 기준으로 연결한다.

## 단계별 진행 현황

1. 프론트 원복 및 작업 기준 정리 완료
2. 관리자 공지사항 구조 분석 및 `/admin/notice` 라우트 추가 완료
3. 관리자 공지사항 JSP 화면 구성 완료
4. 관리자 공지사항 CRUD 연결 완료
5. 검증 및 최종 정리 완료

## 단계별 작업 정리

### 1단계. 프론트 원복 및 작업 기준 정리 완료

- 비즈니스 공지사항 React 라우트와 연결 버튼 작업을 원복했다.
- 관리자 공지사항은 프론트가 아니라 `Backend`의 `AdminController + JSP` 기준으로 다시 잡았다.
- 관리자 메뉴의 `/admin/notice` 링크가 이미 존재하고, 현재 404 원인이 라우트 부재라는 점을 확인했다.

### 2단계. 관리자 공지사항 구조 분석 및 `/admin/notice` 라우트 추가 완료

- `AdminController`에 `GET /admin/notice`를 추가했다.
- `AdminController`에 `GET /admin/notice/detail` 관리자 상세 조회를 추가했다.
- 관리자 상세 조회에서는 조회수가 증가하지 않도록 `NoticeService.findNoticeById()`를 추가했다.
- 목록 화면 진입 시 제목/내용 키워드와 고정 여부 필터를 함께 처리하도록 구성했다.

### 3단계. 관리자 공지사항 JSP 화면 구성 완료

- `WEB-INF/views/admin/admin-notice.jsp`를 생성했다.
- 관리자 공지사항 목록 테이블, 검색 영역, 등록 버튼, 상세 모달, 등록/수정 모달을 구성했다.
- `resources/css/admin-notice.css`를 생성해 관리자 화면 스타일을 추가했다.

### 4단계. 관리자 공지사항 CRUD 연결 완료

- 등록은 `POST /api/notices`로 연결했다.
- 수정은 `PUT /api/notices/{noticeId}`로 연결했다.
- 삭제는 `DELETE /api/notices/{noticeId}`로 연결했다.
- 상세 조회는 관리자 전용 `GET /admin/notice/detail`을 사용하도록 분리했다.
- 공지 등록/수정 시 제목, 내용, 고정 여부를 입력할 수 있게 했다.

### 5단계. 검증 및 최종 정리 완료

- 관리자 공지 관련 파일과 라우트가 추가된 것을 코드 기준으로 확인했다.
- 포트폴리오 브랜치의 GitHub Actions에서 백엔드 WAR 패키징과 프론트엔드 프로덕션 빌드가 성공했다.
- 관리자 공지사항 대표 화면은 원본 JSP·CSS 구조를 기준으로 `docs/images`에 정리했다.
- Oracle 연동이 필요한 실제 HTTP 동작 검증은 로컬 실행 환경에서 별도로 수행한다.

## 최종 반영 파일

- `Backend/src/main/java/com/app/controller/AdminController.java`
- `Backend/src/main/java/com/app/service/notice/NoticeService.java`
- `Backend/src/main/java/com/app/service/notice/impl/NoticeServiceImpl.java`
- `Backend/src/main/webapp/WEB-INF/views/admin/admin-notice.jsp`
- `Backend/src/main/webapp/resources/css/admin-notice.css`

## 최종 메모

- 이번 작업은 관리자 `/admin/notice` 404를 해결하는 방향으로 백엔드 JSP 기준으로 재구성했다.
- 프론트 비즈니스 공지 연결 작업은 원복했다.
- 관리자 공지사항 목록 조회, 등록, 수정, 삭제 화면과 API 연결을 완료했다.
- 포트폴리오 브랜치의 백엔드·프론트엔드 빌드가 GitHub Actions에서 통과했다.
