# DISCUSSION

## 프로필

- `PATCH /users/me/body`의 경로를 `/users/me`로 변경한다.

## 설문

- 설문을 별도로 분리한 이유가 있으므로 유지한다.
- 설문 `PATCH` API를 삭제한다.

## 커뮤니티

- `GET /posts/share-draft`를 삭제하고 월드컵 조회 API로 결과를 가져온다. 공유하기를 누르면 글 작성 화면으로 이동하여 월드컵 결과를 게시글로 공유한다.
- `POST /posts/vote`를 삭제하고, `POST /posts`의 요청 DTO에 투표글을 구분하는 항목을 추가한다.
- `GET /posts/{postId}/likes`로 게시글 좋아요 조회를 추가한다.
- `/posts`로 시작하는 모든 엔드포인트의 경로를 `/community/posts`로 변경한다.
- `GET /comments/{commentId}/like`로 댓글 좋아요 조회를 추가한다.

## 알림

- `GET /notification/unread-count`를 삭제한다.
- 알림 읽음 처리 API의 경로에서 `/read`를 제거하고 `PATCH /notifications/{notificationId}`로 변경한다.
- `GET /notifications/stream`을 삭제하고 FCM으로 변경한다.

> 논의 배경: SSE를 사용하면 다른 화면으로 이동했을 때 알림을 받지 못한다는 우려가 있다. FCM이 일정 시간 동안 확인을 재전송한다면 더 적합한 방식일 수 있다.

## 추천

- `POST /recommendations`의 응답 바디에 `GET /recommendations/{requestId}`의 코디 추천 결과를 포함한다.
- 사이즈 추천 API인 `GET /recommendation/size`를 삭제한다.
- `GET /recommendations/{requestId}/messages`를 삭제한다.

## 피팅

- 피팅 엔드포인트의 경로를 `/vton` 기준으로 변경한다. 세부 경로는 추가 논의가 필요하다.
- 자연어 추천 후에만 가상 피팅을 수행한다. 생성된 이미지를 영구 저장하여 추천 결과에서 함께 보여준다.
- 다른 피팅 API를 삭제하고 `POST /vton`만 유지한다.

## 운영

- 운영 API의 Spring과 FastAPI 헬스 체크 방식을 통일한다.
- 응답 바디 형식을 통일한다.
