# Fitzza API Documentation

## 개요

Fitzza 웹 어플리케이션이 사용하는 API의 문서입니다. 

- [OpenAPI 명세서](https://swagger.io/specification/v3.2/)에 따라 작성
- [Scalar](https://scalar.com/)를 사용해서 인터페이스 구성

## 특이사항

### `/api/v1`과 `/api` 접두어 삭제

- `http://example.com/api/v1/auth/signin`
- `http://api.example.com/v1/auth/signin`

스프링부트를 배울 때, 백엔드 주소에 `/api/v1` 접두사를 붙여서 API 서버 URL로 사용했었습니다. 접두사를 사용하는 대신에 `api` 서브도메인을 사용할 수도 있습니다.
 
이번 프로젝트에서는 `api` 서브도메일을 사용하겠습니다. CDN 서버는 Amazon S3 객체 스토리지 서버를 사용하고 고정된 URL이 제공됩니다. API 서버는 ECS on EC2를 사용하고 DuckDNS와 SWAG를 사용해서 DDNS를 설정하고 리버스 프록시를 통해 서브도메인을 설정할 수 있습니다. 