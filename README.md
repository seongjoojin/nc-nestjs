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
