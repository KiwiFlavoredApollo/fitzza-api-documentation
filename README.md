# Fitzza API Documentation

## 개요

Fitzza 웹 어플리케이션이 사용하는 API의 문서입니다. 

- [OpenAPI 명세서](https://swagger.io/specification/v3.2/)에 따라 작성
- [Scalar](https://scalar.com/)를 사용해서 인터페이스 구성

## 수정사항

### `/api/v1`과 `/api` 접두어 삭제

- `http://example.com/api/v1/auth/signin`
- `http://api.example.com/v1/auth/signin`

스프링부트를 배울 때, 백엔드 주소에 `/api/v1` 접두사를 붙여서 API 서버 URL로 사용했었습니다. 접두사를 사용하는 대신에 `api` 서브도메인을 사용할 수도 있습니다.
 
이번 프로젝트에서는 `api` 서브도메일을 사용하겠습니다. CDN 서버는 Amazon S3 객체 스토리지 서버를 사용하고 고정된 URL이 제공됩니다. API 서버는 ECS on EC2를 사용하고 DuckDNS와 SWAG를 사용해서 DDNS를 설정하고 리버스 프록시를 통해 서브도메인을 설정할 수 있습니다. 

### `/auth/refresh`

`/auth/reissue` 대신에 `/auth/refresh` 엔드포인트를 사용하겠습니다. 이 엔드포인트의 목적은 리프레시 토큰을 사용해서 액세스토큰을 새로 발급받는 것입니다. 재발급을 의미하는 `reissue`를 사용하는 것이 잘못된 것은 아니지만, 리프레시(`refresh`) 토큰의 이름을 그대로 사용해야 헷갈리지 않을 것 같습니다.

### `/auth/signin`

회원가입을 할 때 `/auth/signup` 을 사용하고 있고, 같은 단어를 사용하도록 수정했습니다.

### `/auth/signout`

회원가입을 할 때 `/auth/signup` 을 사용하고 있고, 같은 단어를 사용하도록 수정했습니다.

### `/wishlists`

프론트엔드에서는 LikesPage.jsx 라고 되어있습니다. WishlistPage.jsx 로 수정하겠습니다. 

## 문의사항

### Q1. 회원가입 시 아래 엔드포인트가 필요한가

- `/auth/check-mail`
- `/auth/check-nickname`

REST API의 엔드포인트는 원칙적으로 서버의 자원을 가리키고 따라서 명사입니다. 이메일과 사용자이름의 중복여부는 백엔드에서 사용자를 등록하는 과정에서 확인하게 되는데, 중복인 경우에는 `/auth/signup` 엔드포인트의 요청에 대하여 `409 Conflict`상태코드를 반환하고 응답 내부에서 `DUPLICATE_EMAIL` 또는 `DUPLICATE_NICKNAME`를 반환하는 것은 어떤지 문의드립니다.
