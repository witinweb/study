# Angular 2 Beta & Angular Material 1.0

[AngularJS 블로그](https://blog.angularjs.org/)에 포스팅 된  [Angular 2 Beta](https://angular.io) 와 [Angular Material 1.0](https://material.angularjs.org) 릴리즈에 대한 글을 정리하였습니다. 

by : [스키머](http://schemr.tumblr.com)

## [Angular 2 Beta](https://angular.io)

### beta의 의미
- Angular 2를 이용해서 대규모 어플리케이션을 성공적으로 구축할 수 있다고 확신
- 개발자 프리뷰와 알파를 통해 에드워즈, GreenTea(구글 내부 CRM 시스템), 구글 Fiber 등 구글의 대규모 프로젝트와 Ionic2, NativeScript, Batarangle 등의 외부에서 개발중
- 실제로 새로운 Angular 2 코드 기반의 구글 Fiber가 출시

### 시작하기
- [angular.io](https://angular.io/)에 [Quickstart](https://angular.io/docs/ts/latest/quickstart.html)와 [Tutorial](https://angular.io/docs/ts/latest/tutorial/) 을 업데이트
- [developer guides](https://angular.io/docs/ts/latest/guide/) 와 [chetsheet](https://angular.io/docs/ts/latest/guide/cheatsheet.html) 를 통해서 Angular 2의 주요 기능을 확인

### Angular 1 에서 업그레이드
- ngUpgrade
	- 가능한 기존 어플리케이션을 활용하고 Angular 2로 업그레이드 할 수 있도록 지원
	- Angular 1 어플리케이션에서 Angular 1 코드를 수정하지 않고 Angular 2 코드 혼합 사용 가능
	-  참고
		- [thoughtram blog](http://blog.thoughtram.io/categories/angular-2/)
		- [primer on Angular 2](http://antjanus.com/blog/tutorials/the-beginners-preemptive-guide-to-angularjs-2-alpha/)
- ngForward
	- 다운로드 크기에 민감할 경우 Angular 1 과 Angular 2 라이브러리를 동시에 실행 하는것을 방지하기 위해서 Angular 1 어플리케이션에서 Angular 2 문법을 사용 가능하게 함
	- 현재 어플리케이션에서 Angular 2 구문과 스타일을 사용하고 준비가 완료되면 Angular 2의 전체 업그레이드를 단시간에 할수 있음

### 피드백 제시
- [Github](https://github.com/angular/angular/issues), [Stack Overflow](http://stackoverflow.com/questions/tagged/angular2), [Gitter](https://gitter.im/angular/angular) 를 통해서 이슈 제출
- [angular.io](https://angular.io/) 각 페이지 좌측 상단에 ! 아이콘을 클릭하여 개선할 내용 전송

### 진행중인 내용과 향후계획
- Angular 2의 payload 크기 감소
- 개발 프로세스 전반에 걸쳐 쉽게 사용할 수 있는 Angular CLI 개발
- 개발 친화적인 컴포넌트 라우터의 정의와 링크 API 개발
- 애니메이션 지원
- I18n, L10n 지원

----------------------
- ES5/ES6 사용법에 대한 더 많은 문서
- startup / 런타임 성능 개선
- 구성 스타일 가이드
- 단위, 종단 테스트 개선
- 모바일 웹과 모바일 앱에 대한 추가 지원


## [Angular Material 1.0](https://material.angularjs.org)

- 32가지의 코어 UI 컴포넌트를 탑제한 [Angular Material 1.0](https://material.angularjs.org) 라이브러리가 공식적으로 릴리즈
- 문서와 CodePen 샘플 업데이트 
- 전체 문서와 데모 : [http://material.angularjs.org](http://material.angularjs.org)

### 이전 버전과 1.0 버전의 차이점
- stable CSS 와 API surface : 컴포넌트에 대한 API 확정, 변경 계획 없음
- 플랫폼 지원 : IE 11+, 크롬, 사파리, 파이어폭스, 안드로이드 4.2+, iOS 8+ 에서 테스트
- Angular 1.5-ready : AngularJS 1.3 이상에서만 사용 가능, 새 버전으로 업데이트 되어 ngMaterial 컴포넌트 계속 사용 가능
- github [CHANGELOG](https://github.com/angular/material/blob/master/CHANGELOG.md) 에서 0.11 부터 변경된 전체 내용 확인

### 향후계획
- 지속적인 버그 수정, github queue에서 알려진 문제를 통해서 버전 1.0을 정기적으로 업데이트 예정
- 다음 버그 수정버전은 1.0.1 
- 레이아웃을 별도의 라이브러리로 만들고 이미 알려진 flexbox 브라우저 이슈를 개선하여 payload 크기를 줄이는 1.1 버전에 대한 작업 시작 (2016년 초 예정)
- [Material Design Specification](https://www.google.com/design/spec/material-design/introduction.html)의 발전에 따라서 컴포넌트 추가
- Material 애니메이션, 트렌지션, 적응형 레이아웃의 주요 개선과 기능을 추가할 예정
- Angular 2에 대한 Angular Material 1.0의 보완으로 Angular Material 2.x 개발 시작

