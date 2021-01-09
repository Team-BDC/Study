# 1. React와 Django로 웹서비스 뚝딱 만들기!

- Django + Django Rest Framewoork(DRF)로 API 서버를,
- React로 프론트엔드를 개발해보자!

> redux로 상태관리하기?

## 1-1. React 세팅

> create react app 명령어를 사용하면 webpack이나 babel 등이 리액트 프로젝트에 맞게 node_modules안에 세팅된다.
> 만약 꺼내고 싶으면 eject를 사용한다.

## 1-2. Django rest api에 접근하기

### React app 이름이 app이라고 가정한다.

> 장고와 리액트를 연동한다는 것 : 장고에서는 api를 제공해주고, 리액트는 그 api를 받아 렌더링한다는 의미.

- django에서 serializer를 이용, 파이썬 언어를 브라우저가 이해할 수 있는 json 형식으로 바꾸고 rest_framework에서 제공하는 라우터를 이용해 환경을 세팅한다.
- django에서 cors를 이용, script 태그 내에서 다른 도메인 서버(+다른 포트)로 요청할 수 있게 해준다.
- react에서 app/package.json 하단의 proxy를 이용, 장고 앱에 접속할 수 있도록 한다.
  - 개발 포트와 사용자에게 보여지는 포트를 구분하기 위함!

### React + Redux + axios

1. Redux
   > Javascript app을 위한 예측가능한 state coontainer.
   > 최근에는 대규모 프로젝트에서 너무 복잡해지는 MVC구조의 단점을 보완한 Flux 구조를 사용한다.
   > 리덕스는 Flux 패턴을 좀 더 쉬운 형태로 쓸 수 있게 도와주는 라이브러리라고 할 수 있다.

- Redux를 사용하면
  - 컴포넌트 state 관련 로직들을 다른 파일로 분리해, 효율적인 관리 가능
  - 컴포넌트끼리 state 공유할 때 여러 컴포넌트 거치지 않아도 ok
  - 미들웨어를 이용해 비동기 작업, 로깅 등 확장 작업 쉽게 가능
- Flux : client-side 웹 구축시 사용하는 앱구조, 디자인 패턴. 단방향 데이터 흐름의 구조.

2. axios
   - HTTP 클라이언트 라이브러리. 비동기 방식으로 HTTP 데이터를 요청한다. 즉 데이터 처리. 내부적으로 Axios는 직접 XMHttpRequest를 다루지 않고 'AJAX 호출'를 한다.
   - AJAX : 비동기 자바스크립트와 XML. 서버와 통신하기 위해 XMLHttpRequest 객체를 사용하는 것.
     비동기성을 통해 전체 페이지가 아닌 일부분만 업데이트 할 수 있다.
     > xios가 REST api에 HTTP 요청(GET 요청만) -> 결과값은 response -> API 구조를 안다면 JSON 형식으로 불러올 수 있다.
     > 페이지 새로고침없이 서버에 요청 가능 + 서버로부터 데이터 받고 작업 수행
   - django는 템플릿에서 CSRF에 대한 토큰 방식을 제공해주지만, 리액트를 통해 템플릿을 처리하므로 403 에러 발생 가능성이 있다. 이때 axios 모듈을 사용하면 간단하게 철할 수 있다.
