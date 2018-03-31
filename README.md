# React-router 학습

```
react-router 는, 써드파티 라이브러리로서, 비록 공식은 아니지만 (페이스북 공식 라우팅 라이브러리는 존재하지 않습니다) 가장 많이 사용되고 있는 라이브러리이다. 이 라이브러리는 클라이언트 사이드에서 이뤄지는 라우팅을 간단하게 해준다. 게다가 서버 사이드 렌더링도 도와주는 도구들이 함께 딸려온다. 추가적으로 이 라우터는 react-native 에서도 사용 될 수 있다.

여러 화면으로 구성된 웹 어플리케이션을 만들게 된다면, react-router 는 필수 라이브러리다.

```

## 필수 설치 라이브러리

```
$ yarn add react-router-dom
-> 브라우저에서 사용되는 리액트 라우터
$ yarn add cross-env --dev
->프로젝트에서 NODE_PATH 를 사용하여 절대경로로 파일을 불러오기 위하여 환경 변수를 설정 할 때 운영체제마다 방식이 다르므로 공통적인 방법으로 설정 할 수 있게 해주는 라이브러리다.
$ yarn add query-string
-> url 쿼리를 해석해서 객체로 만들어주는 기능을 한다.

```

## 디렉토리 구성

```
src/components: 컴포넌트들이 위치하는 디렉토리입니다.
src/pages: 각 라우트들이 위치하는 디렉토리 입니다.
src/client: 브라우저 측에서 사용할 최상위 컴포넌트 입니다. 우리가 추후 서버사이드 렌더링을 구현 할 것이기 때문에 디렉토리를 따로 구분하였습니다. (서버사이드 렌더링을 할 때에는 서버 전용 라우터를 써야합니다.) 여기서 라우터를 설정합니다.
src/server: 서버측에서 사용 할 리액트 관련 코드를 여기에 넣습니다.
src/shared: 서버와 클라이언트에서 공용으로 사용되는 컴포넌트 App.js 가 여기에 위치합니다.
src/lib: 나중에 웹 연동을 구현 할 때 사용 할 API와 코드스플리팅 할 때 필요한 코드가 여기에 위치합니다.

```

## NODE_ENV 설정
```javaScript
"scripts": {
  "start": "cross-env NODE_PATH=src react-scripts start",
  "build": "cross-env NODE_PATH=src react-scripts build",
  "test": "react-scripts test --env=jsdom",
  "eject": "react-scripts eject"
}
```

### 라우트에서 사용하는 props

+ ***history*** 이 객체를 통해 push, replace 를 통해 다른 경로로 이동하거나 앞 뒤 페이지로 전환 할 수 있습니다.
+ ***location*** 이 객체는 현재 경로에 대한 정보를 지니고 있고 URL 쿼리 (/about?foo=bar 형식) 정보도 가지고있습니다.
+ ***match*** 이 객체에는 어떤 라우트에 매칭이 되었는지에 대한 정보가 있고 params (/about/:name 형식) 정보를 가지고있습니다.
