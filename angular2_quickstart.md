# Angular 2 Quickstart 

[Angular 2](https://angular.io) 를 간단히 시작할 수 있는 [5Min Quickstart](https://angular.io/docs/js/latest/quickstart.html)를 TypeScript, JavaScript(ES5), Dart 세가지 언어로 제공합니다.  (타이틀 밑에 콤보박스를 이용해서 선택할 수 있습니다)
이 글은 [JavaScript Quickstart](https://angular.io/docs/js/latest/quickstart.html)를 번역 하였습니다. (몇군데 불필요한 부분은 생략하였습니다.) 

## 예제
plunker를 이용해서 구현된 [예제](https://angular.io/resources/live-examples/quickstart/js/plnkr.html)를 제공합니다. 

## 파일구조
    angular2-quickstart
     |-- app
        |-- app.component.js
        |-- boot.js
     |-- index.html
     |-- license.md
     
## 개발 환경
npm 패키지 매니저를 이용해서 angular 2 라이브러리를 설치할 수 있습니다. 
angular2-quickstart 폴더를 생성 후 아래의 내용으로 package.json 파일을 생성합니다. 

### package.json(dependencies)
    {
      "name": "angular2-quickstart",
      "version": "1.0.0",
      "scripts": {
        "start": "npm run lite",
        "lite": "lite-server"
      },
      "license": "ISC",
      "dependencies": {
        "angular2": "2.0.0-beta.0",
        "systemjs": "0.19.6",
        "es6-promise": "^3.0.2",
        "es6-shim": "^0.33.3",
        "reflect-metadata": "0.1.2",
        "rxjs": "5.0.0-beta.0",
        "zone.js": "0.5.10"
      },
      "devDependencies": {
        "lite-server": "^1.3.1"
      }
    }

scripts 부분에 사용되고 있는 lite-server 는 경량화된 정적 파일 서버로, 라우팅을 사용하는 angular 어플리케이션에의 작성과 유지보수에 우수한 지원을 합니다. 
package.json 파일 생성 후 npm 명령어를 통해서 패키지를 설치합니다. 설치중에 error 메시지가 많이 나오는데 무시하면 됩니다. 

    npm install

## 컴포넌트 추가
app 폴더에 app.component.js 파일을 생성합니다. 

    (function(app) {
      app.AppComponent = ng.core
        .Component({
          selector: 'my-app',
          template: '<h1>My First Angular 2 App</h1>'
        })
        .Class({
          constructor: function() {}
        });
    })(window.app || (window.app = {}));

**ngCore**에 포함되어 있는 **Component** 와 **Class** 메소드를 체이닝 하여 **AppComponent**를 생성합니다. 
**Component** 메서드는 두개의 속성으로 객체 구성을 합니다.  **Class** 메서드는 컴포넌트 자체를 구현하는 곳이며, 뷰에 바인딩 속성과 메서드를 제공하고 UI 부분에 사용하는 것이 적당합니다. 

## 모듈
Angular 어플리케이션은 모듈화 되어 있으며, 많은 파일들이 각각의 목적을 갖고 구성되어 있습니다. ES5 JavaScript는 모듈을 가지고 있지 않으므로, IIFE("Imeediately Invoked Function Expression : 즉시실행 함수표현식") 을 이용해서 코드를 감싸고 있습니다. **app** 'namespace' 객체를 인자로 받아서 **window.app** 이 존재할때, 존재하지 않는다면 빈 객체로 초기화 하여 즉시실행 함수를 호출합니다. 

    (function(app) {
    /* . . . */
    })(window.app || (window.app = {}));

더 복잡한 어플리케이션에서는 **appComponent** 의 자식 컴포넌트를 가질 것이고, 더 많은 파일과 모듈을 가질 것입니다. 

Quickstart는 복잡한 어플리케이션이 아니므로 하나의 컴포넌트면 충분합니다. 

모듈은 다른 모듈에 의존적 입니다. Angular JavaScript 어플리케이션에서는 또 다른 모듈이 제공하는 어떤것을 필요로 할때, app 객체로 부터 얻을 수 있습니다. 다른 모듈이 **AppComponent**를 참조 할 필요가 있을때는, 아래와 같이**app.AppComponent**에서 가져옵니다.

    ng.platform.browser.bootstrap(app.AppComponent);

Angular는 또한 라이브러리 모듈의 집합입니다. 각 라이브러리는 여러 관련된 기능을 모듈로 구성한 모듈 자체 입니다.

Angular에서  어떤것을 필요로 할때, **ng** 객체를 사용합니다.

## Class 정의 객체

파일의 밑에 비어 있는 부분이 **AppComponent** 클래스의 정의 객체 입니다. 어플리케이션을 빌드할 준비가 되면, 속성과 어플리케이션 로직이 객체를 확장 할 수 있습니다. Quickstart에서는 아무것도 할 필요가 없기 때문에 **AppComponent** 클래스에는 비어 있습니다. 

     .Class({
          constructor: function() {}
        });

## Component 정의 객체
**ng.core.Component()** 를 사용하여 이 클래스 정의 객체가 Angular 컴포넌트라는 것을 알려줍니다. **ng.core.Component()** 메서드는 **selector**와 **template**, 두개의 필드를 환경설정 객체에 전달됩니다.

     .Component({
          selector: 'my-app',
          template: '<h1>My First Angular 2 App</h1>'
        })

**selector**는 **my-app**이라는 이름의 HTML엘리먼트에 대한 간단한 CSS 선택자를 지정합니다. Angular는 HTML안에 **my-app** 엘리먼트를 어디서든지 **AppComponent**의 인스턴스를 만들고 보여줍니다.

 **template**은 HTML의 형태로 어떻게 뷰를 렌더링 하는지를 알려줍니다. 여기에서는 "My First Angular App" 의 한줄의 HTML을 알려줍니다.
이제 Angular에서 이 컴포넌트를 로드하기 위해서 어떤것이 필요한지 알아보겠습니다.

## Give it the boot
**app/** 폴더에 **boot.js** 파일을 만들고 아래와 같이 작성합니다.

    (function(app) {
      document.addEventListener('DOMContentLoaded', function() {
        ng.platform.browser.bootstrap(app.AppComponent);
      });
    })(window.app || (window.app = {}));

어플리케이션을 실행하기 위해서 두가지가 필요합니다.
1. Angular의 browser **bootstrap** 함수
2. 작성한 어플리케이션 루트 컴포넌트

'namespaces'에 위의 두가지를 가지고 있습니다. 그 다음 루트 컴포넌트인 **appComponent** 를 전달하는 **bootstrap** 을 호출합니다. 

> 아래의 Appendix: boot.js에서 boot.js 파일을 만든 이유와 ng.platform.browser에서
> bootstrap이 필요한 이유를 알아 봅니다.

루트에 Angular 어플리케이션을 실행하기 위해서 컴포넌트를 브라우저에 요청했습니다. 

##index.html 추가
Angular는 특정 위치의 **index.html**을 보여줍니다. 이 파일을 생성합니다.
**index.html**은 **프로젝트의 루트폴더**에 위치해야 합니다. 다음과 같이 **index.html** 을 생성합니다.

     <html>
    
      <head>
        <title>Angular 2 QuickStart</title>
    
        <!-- 1. Load libraries -->
        <script src="node_modules/angular2/bundles/angular2-polyfills.js"></script>
        <script src="node_modules/rxjs/bundles/Rx.umd.js"></script>
        <script src="node_modules/angular2/bundles/angular2-all.umd.js"></script>
    
        <!-- 2. Load our 'modules' -->
        <script src='app/app.component.js'></script>
        <script src='app/boot.js'></script>
    
      </head>
    
      <!-- 3. Display the application -->
      <body>
        <my-app>Loading...</my-app>
      </body>
    
    </html>

HTML에서 세 가지 주목할 부분이 있습니다.
1. Angular 2 에서 필요한 **angular2-polyfills.js**와 **Rx.js** JavaScript 라이브러리를 로드합니다. 
2.  작성한 JavaScript 파일을 로드합니다. 순서가 중요한데, **boot.js** 가 먼저 작성되어야 합니다.
3. <body> 안에 <my-app> 태그를 추가합니다.  이것이 이 어플리케이션의 영역 입니다. 

Angular가 **boot.js**파일의 **bootstrap** 함수를 호출하면, **AppComponent** 메타 데이터를 읽어 **my-app** 셀렉터를 찾고, **my-app** 이름의 엘리먼트 태그의 위치를 찾아서 어플리케이션의 태그 사이에 로드합니다. 

##컴파일과 실행!

터미널을 열어서 다음 명령어를 실행합니다. 

    npm start

이 명령어는 브라우저에서 **index.html**을 로드하고 어플리케이션 파일이 변경될때 브라우저가 새로고침되어 반영되는 **lite-server** 라는 정적 서버를 실행합니다.

잠시후 브라우저 탭이 열리고 화면에 **"My First Angular 2 App"** 이 표시됩니다.

> 만약 Loading... 이 계속 표시 된다면, **[Appendix: Browser ES6
> support](#Appendix:%20Browser%20ES6%20support)**을 참고하세요.

## 일부의 변경
"My SECOND Angular 2 app" 이라고 메세지를 수정해 보세요.
lite-server 는 감시하고 있다가 변경이 있으면 브라우저를 새로고침 합니다. 그리고 수정된 내용을 보여줍니다. 
이것은 어플리케이션 개발을 할때 매력적인 방법입니다. 

## 부록
부록의 내용은 필수가 아니며 호기심이 있다면 참고하세요.

## Appendix: Browser ES6 support
Angular 2는 일부 ES2015의 기능에 의존하고, 그것중에 대부분은 최신 브라우저에서만 가능합니다. 몇몇 브라우저(IE11 포함)에서 필요한 기능을 지원하기 위해서 **shim**이 필요합니다. **index.html**에서 다른 스크립트 위에 다음과 같이 **shim**을 포함시키세요.

    <script src="node_modules/es6-shim/es6-shim.js"></script>

## Appendix: boot.js
Bootstrapping is platform-specific

We use the bootstrap function from ng.platform.browser, not ng.core. There's a good reason.

We only call "core" those capabilities that are the same across all platform targets. True, most Angular applications run only in a browser and we'll call the bootstrap function from this library most of the time. It's pretty "core" if we're always writing for a browser.

But it is possible to load a component in a different enviroment. We might load it on a mobile device with Apache Cordova We might wish to render the first page of our application on the server to improve launch performance or facilitate SEO.

These targets require a different kind of bootstrap function that we'd import from a different library.

Why do we create a separate boot.js file?

The boot.js file is tiny. This is just a QuickStart. We could have folded its few lines into the app.component.js file and spared ourselves some complexity.

We didn't for what we believe to be good reasons:

Doing it right is easy
Testability
Reusability
Separation of concerns
We learned about import and export
It's easy

Sure it's an extra step and an extra file. How hard is that in the scheme of things?

We'll see that a separate boot.js is beneficial for most apps even if it isn't critical for the QuickStart. Let's develop good habits now while the cost is low.

Testability

We should be thinking about testability from the beginning even if we know we'll never test the QuickStart.

It is difficult to unit test a component when there is a call to bootstrap in the same file. As soon as we load the component file to test the component, the bootstrap function tries to load the application in the browser. It throws an error because we're not expecting to run the entire application, just test the component.

Relocating the bootstrap function to boot.js eliminates this spurious error and leaves us with a clean component module file.

Reusability

We refactor, rename, and relocate files as our application evolves. We can't do any of those things while the file calls bootstrap. we can't move it. We can't reuse the component in another application. We can't pre-render the component on the server for better performance.

Separation of concerns

A component's responsibility is to present and manage a view.

Launching the application has nothing to do with view management. That's a separate concern. The friction we're encountering in testing and reuse stems from this unnecessary mix of responsibilities.

Import/Export

While writing a separate boot.js file we learned an essential Angular skill: how to 'export' from one 'module' and 'import' into another via our simple namespace abstraction. We'll do a lot of that as we learn more Angular.