# CHANGELOG

## 개요

API 명세서는 [WBS 요구사항 정의서](https://docs.google.com/spreadsheets/d/11iPQ3YFhEUBNp-2VAse4qQpHFEm6ymTOGz5_9-XCA6Y/edit?gid=308248600#gid=308248600)을 기반으로 작성되었습니다. 경로는 별도 표기가 없으면 `/api` 접두어 제거 후를 기준으로 합니다.

## 수정사항

### 공통

- [삭제] 공개 API 경로의 `/api` 접두어
- [변경] Gateway 인증 설명: `/auth/**`는 토큰 검증 없이 통과

### 회원 및 인증

- [변경] `POST /users/signup` → `POST /auth/signup`
- [변경] `POST /auth/login` → `POST /auth/signin`
- [변경] `POST /auth/logout` → `POST /auth/signout`
- [변경] `POST /auth/reissue` → `POST /auth/refresh`
- [삭제] `GET /users/check-email`
- [삭제] `GET /users/check-nickname`
- [변경] 이메일 중복 확인을 회원가입 시 검사로 통합
- [변경] 닉네임 중복 확인을 회원가입 시 검사로 통합
- [변경] 회원가입 `409` 응답 스키마 → `SignupConflict`
- [추가] 회원가입 중복 응답 스키마 `SignupConflict`
- [추가] 이메일·닉네임 중복 공통 코드 `DUPLICATE_VALUE`
- [추가] 중복 필드와 원인을 반환하는 `errors` 배열
- [추가] 이메일만 중복된 회원가입 응답 예시
- [추가] 닉네임만 중복된 회원가입 응답 예시
- [추가] 이메일·닉네임 모두 중복된 회원가입 응답 예시

### 프로필

- [삭제] `GET /users/profile/options`
- [변경] `PATCH /users/me/body` → `PATCH /users/me`

### 설문

- [삭제] `PATCH /surveys/{surveyId}`

### 커뮤니티

- [변경] `/posts`로 시작하는 경로 → `/community/posts`
- [삭제] `POST /posts/images`
- [삭제] `GET /community/posts/share-draft`
- [삭제] `POST /community/posts/vote`
- [추가] `GET /community/posts/{postId}/likes`

### 투표

- [변경] `POST /posts/{postId}/votes` → `POST /community/posts/{postId}/poll/votes`
- [변경] `GET /posts/{postId}/votes` → `GET /community/posts/{postId}/poll`
- [변경] `POST /posts/{postId}/votes/close` → `PATCH /community/posts/{postId}/poll`

### 댓글

- [추가] `GET /comments/{commentId}/like`

### 알림

- [삭제] `GET /notifications/unread-count`
- [삭제] `GET /notifications/stream`
- [변경] `PATCH /notifications/{notificationId}/read` → `PATCH /notifications/{notificationId}`

### 추천

- [삭제] `GET /recommendations/size`
- [삭제] `GET /recommendations/{requestId}/messages`
- [변경] `POST /recommendations` 응답 바디를 `GET /recommendations/{requestId}`와 동일하게 수정

### 피팅

- [변경] `POST /fittings` → `POST /vton`
- [삭제] `GET /fittings/candidates`
- [삭제] `POST /fittings/candidates`
- [삭제] `DELETE /fittings/candidates/{productId}`
- [삭제] `POST /fittings/photos`
- [삭제] `GET /fittings`
- [삭제] `GET /fittings/{fittingId}`

### 운영 API

- [변경] Spring·FastAPI 헬스 체크 경로를 `GET /actuator/health`로 통일
- [삭제] `GET /health`
- [삭제] `GET /ready`
