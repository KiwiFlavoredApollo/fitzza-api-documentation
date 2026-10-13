# DISCUSSION

프로필 patch users/me/body -> users/me

설문 필요해서 나눠놓은 이유가 있어서 유지 원함

설문 PATCH 빼기

커뮤니티 Get /posts/share-draft : 월드컵 결과를 게시글 공유하기
ㄴ 공유하기 누르면 글을 쓰는 화면으로 넘어가서 작성
이 API 빼고 월드컵에서 Get 받아오는 걸로

커뮤니티 Post /posts/vote  없애고 posts에 투표글 구분해서 넣는 dto 추가하기

커뮤니티 Get /posts/{postId}/likes 로 게시글 좋아요 조회 추가

posts로 시작하는 엔드포인트를 /community/posts 로 다 바꾸기

커뮤니티 Get comments/{commentId}/like 로 댓글 좋아요 조회 추가

알림 Get /notification/unread-count API 삭제

알림 Patch /notifications/{notificationId} 로 URL 변경 read 삭제

알림 알림실시간 구독 SSE 사용하게 되면 , 다른데 다녀오면 알림 못 받는다.
FCM 을 쓰면 일정 시간 안에는 계속 확인을 보내준다... 라고 하면 그게 좀 더 적합한 기능
Get /notifications/stream -> 삭제후 FCM 으로 수정


추천 Post reponse body post/recommendations 에 Get의 /recommendations/{requestId} 코디추천결과 넣어주기
사이즈 추천 Get /recommendation/size 삭제 , Get /recommendations/{requestId}/messages 삭제

피팅 /vton/'' 으로 엔드포인트 이름이 달라져야합니다.

자연어 추천 후에만 가상피팅을 하는데 , 생성된 이미지를 영구저장해서 추천 결과에서 같이 보여줄 수 있도록 해야함

다른 거 다 지우고 post/vton 남기기

운영 API 에 Spring health check 에 FastAPI 통일시키기 , body 형식 통일하기