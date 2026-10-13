# Fitzza API Documentation

## 개요

Fitzza 웹 어플리케이션이 사용하는 API의 문서입니다. 

- [OpenAPI 명세서](https://swagger.io/specification/v3.2/)에 따라 작성
- [Scalar](https://scalar.com/)를 사용해서 인터페이스 구성

## 수정사항

### `/status/xxx-service`

`/xxx/status` 에서 `/status/xxx-service` 로 수정하였습니다. `/status/xxx-service` 를 사용하면 백엔드의 특정 "서비스"의 상태를 가져온다는 의미를 강하게 전달할 수 있을 것 같습니다.

### `/internal/users/{userId}/wishlists`으로 변경

`/internal/wishlists/check`에서 `/internal/users/{userId}/wishlists`으로 변경하였습니다. [WishlistController가 product-service에 있는 이유가 무엇인가요? - GitHub](https://github.com/duckfairy-wak/fitzza_msa_finalproject/issues/13)와 연관이 있는데, `/wishlists` 엔드포인트를 user-service에서 관리하는 것을 전제로 수정하였습니다. 

엑세스토큰을 포함해서 요청을 보내는 것이 아니기 때문에 userId를 경로변수로 전달합니다. 

## 문의사항

### Q2. 프로필 선택지가 필요한 이유가 무엇인가

깃허브 이슈 페이지로 이동하였습니다.

### Q3. `/users/me`에서 `shoeSize` 대신에 `footLength`를 사용하는 것은 어떤가

`body` 아래 `height`, `weight` 등의 값은 신체 치수를 나타냅니다. 하지만 `shoeSize`는 신체 치수가 아니라 신발의 크기를 의미하고 `body`라는 카테고리로 묶기에는 이상하다고 느꼈습니다. 하지만 신발 크기가 곧 발 크기를 의미하는 것임은 당연하기 때문에, 무신사 API 등을 참고하는 등으로 특별한 이유가 있는지 궁금합니다.

### Q4. `/users/me`에서 `bodyType`이 있는 이유가 무엇인가

사용자로부터 `height`와 `weight` 값을 입력받는데, 여기서 `bodyType`을 계산할 수 있지 않은가요. 사용자가 모순되는 입력을 할 수도 있습니다. 예를 들어 키 150cm, 몸무게 90kg 그리고 체형을 SLIM 이라고 입력하는 경우입니다.

### Q5. `/users/me` 응답 구조

```json
{
  "email": "string",
  "nickname": "string",
  "body": {
    "height": 175,
    "weight": 70,
    "gender": "W",
    "bodyType": "SLIM",
    "preferredFit": "REGULAR",
    "preferredStyles": [
      "CASUAL"
    ],
    "shoeSize": 270
  }
}
```
`preferredFit`과 `preferredStyles`등이 `body`라는 카테고리 아래에 있는 것이 과연 맞는지 모르겠습니다. 

`gender`는 Woman/Man이 아니라 Male/Female로 하는 것으로 건의드립니다. 성별도 `body`라는 카테고리 아래에 있는 것이 맞는지 잘 모르겠습니다.

`bodyType`, `preferredFit` 그리고 `preferredStyles`는 `/users/profile/optioins` 엔드포인트에서 하나의 카테고리로 묶이는 것 같습니다. `options`와 같은 별도 카테로리를 만드는 것을 건의드립니다.

```json
{
  "email": "string",
  "nickname": "string",
  "gender": "W",
  "body": {
    "height": 175,
    "weight": 70,
    "shoeSize": 270
  },
  "options": {
    "bodyType": "SLIM",
    "preferredFit": "REGULAR",
    "preferredStyles": [
      "CASUAL"
    ]
  }
}
```

아니면 카테고리를 없애고 평면적으로 만드는 것을 건의드립니다.

```json
{
  "email": "string",
  "nickname": "string",
  "gender": "W",
  "height": 175,
  "weight": 70,
  "shoeSize": 270,
  "bodyType": "SLIM",
  "preferredFit": "REGULAR",
  "preferredStyles": [
    "CASUAL"
  ]
}
```

### Q8. review-service가 따로 있는 이유는 무엇인가

`/reviews` 엔드포인트가 상품에 대한 리뷰를 불러오는 것이라면 product-service에서 관리하면 될 것 같다고 생각했습니다. 별도 서비스로 분리한 이유가 있는지 궁금합니다.

## 참고문헌

- [상품 데이터 - Pastes.io](https://pastes.io/0fKqRy7P)