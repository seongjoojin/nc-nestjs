# nc-nestjs

NestJS로 API 만들기

## 0 INTRODUCTION

### 0.3 Project Setup

```bash
$ npm i -g @nestjs/cli
$ nest new
```

## 1 ARCHITECTURE OF NESTJS

### 1.0 Overview

NestJS는 mina.ts 파일을 가짐

NestJS는 데코레이터랑 함께 함

데코레이터는 클래스에 함수기능을 추가할 수 있기 때문

### 1.1 Controllers

- 앱 모듈은 모든 것의 루트 모듈과 같은 것
- 모듈 : 어플리케이션의 일부분
- 중요한 것 : controller랑 나머지 하나는 provider
- controller : 기본적으로 url을 가져오고 함수를 실행함 -> express의 라우터 같은 존재
- 데코레이터는 꾸며주는 함수나 클래스랑 붙어있어야 됨.

### 1.2 Services

- Nest JS는 콘트롤러를 비즈니스 로직이랑 구분 시키고 싶어함
- 컨트롤러는 url를 가져오는 역할과 함수를 실행
- 나머지 비즈니스 로직은 서비스로 감
- 서비스는 일반적으로 실제 function을 가지는 부분

## 2 REST API

### 2.0 Movies Controller

```bash
$ nest g co
```

parameter의 decorator를 사용하면
NestJS가 url이 있는 id parameter를 원하는 걸 앎

일부 사람들은 put을 이용하지 않아도 된다고 함
put은 모든 리소스를 업데이트 하기 때문임

patch는 리소스의 일부분만 업데이트 해줌

### 2.2 Movies Service part One

https://en.wikipedia.org/wiki/Single-responsibility_principle

하나의 module, class 혹은 function이 하나의 기능은 꼭 책임져야한다는 것.

서비스는 로직을 관리하는 역할을 가지게 될 것

```bash
$ nest g s
```

### 2.4 DTOs and Validation part One

DTO는 데이터 전송 객체(Data Transfer Object)를 뜻함.

DTO쓰는 한가지 이유는 프로그래머로서 코드를 더 간결하게 만들 수 있도록 해줌
NestJS가 들어오는 쿼리에 대해 유효성을 검사할 수 있게 해줌

일반적으로 파이프는 미들웨어같은 거라고 생각할 수 있음

```bash
$ npm i class-validator class-transformer
```

https://docs.nestjs.com/pipes#global-scoped-pipes

### 2.5 DTOs and Validation part Two

```bash
$ npm i @nestjs/mapped-types
```

mapped-types은 타입을 변환시키고 사용할 수 있게 하는 패키지임

### 2.6 Modules and Dependency Injection

app.module은 AppController랑 AppProvider만 가지고 있어야함.

movie.module에 MoviesController, MoviesService에 옮김

NestJS에서 앱은 여러 개의 모듈로 구성되게됨

```bash
$ nest g mo
```

```bash
$ nest g co
```

Nest에서는 dependency injection이라 부르는 것이 있음.

https://docs.nestjs.com/providers
https://medium.com/teamzerolabs/introduction-to-nestjs-dependency-injections-in-typescript-94e1154f40c

### 2.7 Express on NestJS

NestJS는 Express 위에서 돌아감

컨트롤러에서 Request, Response 객체가 필요하면 사용할 수 있음

https://docs.nestjs.com/controllers#request-object

req나 res 같은 Express객체를 직접적으로 사용하는게 좋은 방법은 아님
왜냐하면 NestJS는 두 개의 프레임워크랑 작동하기 때문임

기본적으로 Express 위에서 실행되는데 이걸 Fastify 라는 걸로 전환시킬 수 있음
https://www.fastify.io/
https://docs.nestjs.com/techniques/performance#performance-fastify

중요한 건 NestJS가 두 프레임워크 위에서 동시에 돌아간다는 것임

## 3 UNIT TESTING

### 3.0 Introduction to Testing in Nest

jset는 자바스크립트를 아주 쉽게 테스팅하는 npm패키지임

.spec.ts는 테스트를 포함한 파일임

nestjs에서는 jest가 .spec.ts 파일들을 찾아볼 수 있도록 설정되어 있음.

유닛(단위) 테스팅 : 모든 function을 따로 테스트 하는 것임.

두 가지의 테스팅 종류

- 유닛 테스팅 : 서비스에서 분리된 유닛을 테스트
- end-to-end(e2e) 테스트 : 모든 시스템을 테스팅

유닛 테스팅 => function 하나 하나를 따로 테스팅하는 유닛 테스팅
e2e테스팅 => 이 페이지를 가면 특정 페이지가 나와야하는 경우 사용, 사용자가 취할만한 액션들을 처음부터 끝까지 테스트
