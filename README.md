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
