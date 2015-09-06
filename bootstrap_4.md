# Bootstrap 4 에서 달라진 점들

by [스키머](http://schemr.tumblr.com/)

![enter image description here](https://lh3.googleusercontent.com/-ItnMFXF7KKs/Vev4-NcZuGI/AAAAAAAAA90/Kftsv8g3aaw/s0/bs4-alpha.png "bs4-alpha.png")

지난달(2015.08) 18일 [부트스트랩 4 alpha](http://v4-alpha.getbootstrap.com/)가 릴리즈 되었습니다. 
블로그에 공개된 부트스트랩 4에서 달라진 점들을 간단히 살펴보겠습니다.

## LESS 에서 SASS로 이동
부트스트랩 4에서 가장 큰 변화는 LESS에서 SASS로의 이동입니다. 
[Libsass](http://sass-lang.com/libsass) 엔진을 통해서 더 빠른 컴파일을 기대하고 있습니다. 
transitions과 gradients 등의 모든 변수들의 옵션을 하나의 파일로 모으고 Sass 변수로 커스텀 할 수 있습니다. 

## 향상된 Grid 시스템
새로운 계층을 통해서 모바일 디바이스에 대한 더나은 Grid 시스템을 제공합니다. 
또한 pixel 대신에 rem과 em을 사용합니다. 자세한 사항은 아래 표를 참고하세요.

![enter image description here](https://lh3.googleusercontent.com/-pvtw6IAocz0/Veq0gOc08NI/AAAAAAAAA9I/kR4wUm_4IPE/s0/bootstrap4.jpg "grid system")  

## IE8 지원 중단
media queries 를 지원하지 않는 ie8의 문제점과 pixel에서 rem, em으로의 이동으로 ie8의 지원을 중단합니다. ie8의 지원이 필요하다면 부트스트랩 3를 이용해야 합니다. 
 
## Opt-in Flexbox 지원
 Flexbox는 기본적으로 CSS의 유연한 레이아웃 옵션 입니다.
 부트스트랩 4에서 다음의 3단계를 통해서 Flexbox 모드를 활성화 시킬수 있습니다. 
 - scss 파일을 열어서 $enable-flex  변수를 찾습니다.
 - false에서 true로 바꿉니다.
 - 다시 컴파일을 하고 모든 그리드 컴포넌트들을 Flexbox로 바꿉니다.
 
## Cards 컴포넌트
Wells,  panels 그리고 thumbnails 컴포넌트를 대체하여 카드 컴포넌트를 추가 하였습니다.

## Normalize.css 에서 Reboot.css 로 변경
일반적인 HTML 엘리먼트 스타일의 reset 으로 Normalize.css 에 box-sizing과 같은 추가적인 규칙을 추가하여 부트스트랩에서 더 쉽게 사용할수 있도록 해줍니다.

## Tooltip 및 Popovers의 향상된 자동 배치
[Tether](http://github.hubspot.com/tether/) 라는 서드파티 라이브러리를 통해서 Tooltip 및 Popovers 기능을 향상 시켰습니다.

## 자바스크립트 플러그인 코드 재작성
ES6에서 모든 자바스크립트 플러그인 코드를 재작성 하여 성능을 향상시켰습니다. 또한 UMD 지원, 메소드, 옵션을 추가 하였습니다.

## 부트스트랩 3에 대한 지원
부트스트랩 3 이 나왔을때는 v2.x 에 대한 모든 지원을 즉시 중지하여 많은 사용자들에게 고통을 주었지만 부트스트랩 3에 대한 중요한 버그의 수정 및 문서의 향상을 유지합니다. 


이외에도 예제 및 코드, 검색에 대한 Documents를 향상 시키고 table에 'Inverse' 클래스 등의 내용이 추가 되었습니다. 

아직은 알파 버전이기 때문에 바로 사용은 힘들지만, 향상된 부트스트랩을 기대해 볼 수 있을것 같습니다. 



참고
- 부트스트랩 4 alpha (http://v4-alpha.getbootstrap.com/)
- 부트스트랩 블로그 (http://blog.getbootstrap.com/2015/08/19/bootstrap-4-alpha/)
- github (https://github.com/twbs/bootstrap/tree/v4-dev)

