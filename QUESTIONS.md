# QUESTIONS

## Q. `PATCH /users/me/body`가 필요한가
사용자 정보를 수정하는 것이라면 `PATCH /users/me`를 사용해도 되지 않은가

## Q. `POST /posts/vote`가 필요한가
투표 게시글을 작성하는 엔드포인트가 따로 있는데, `POST /posts` 엔드포인트를 사용하고 요청 바디에 `type` 항목을 전달받아서 일반 게시글과 투표 게시글을 구별할 수 있지 않은가

## Q. `GET /posts/share-draft`의 용도가 무엇인가