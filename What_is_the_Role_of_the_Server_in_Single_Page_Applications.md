## AngularJS - [단일페이지 어플리케이션(SPA) 에서 서버의 역할은 무엇인가?](http://weblogs.asp.net/dwahlin/what-s-the-role-of-the-server-in-single-page-applications-spas)

AngularJS를 처음 사용하신다면 우선 60분 가량의 영상인 [AngularJS in 60-ish Minutes](http://weblogs.asp.net/dwahlin/archive/2013/04/12/video-tutorial-angularjs-fundamentals-in-60-ish-minutes.aspx)를 보시길 권합니다. 제가 만든 [AngularJS JumpStart](https://weblogs.asp.net/dwahlin/the-angularjs-jumpstart-video-training-course-has-been-released) 영상도 보시길 바랍니다. 

저는 최근 AngularJS에 대한 상담과 교육을 많이하고 있는데요 끊임없이 받는 질문이 있습니다: "단일페이지 어플리케이션(Single Page Applications)에서 서버의 역할은 무엇인가요?" 여러분의 사용하는 SPA 프레임워크(AngularJS](http://angularjs.org/), [Ember](http://emberjs.com/), [Durandal](http://durandaljs.com/), 등등)이 무엇이건 간에 서버의 데이터 처리를 위한 서비스(RESTful이든 아니든간에)에 의존하게 됩니다. 이것이 서버가 SPA와 함께 구동되는 분명한 역할입니다.

### 데이터 서비스 Data Service

이것은 확실히 대부분의 사람들이 생각하는 SPA를 실행하는 서버의 가장 일반적인 역할입니다. 서버는 일반적으로 데이터의 GET, PUT, POST, DELETE 를 쉽게 사용할수 있도록 SPA클라이언트에 RESTful 서비스를 제공합니다.  이것은 Node.js, ASP.NET Web API, PHP, Firebase와 같은 클라우드 서비스, 그리고 HTTP, 웹 소켓, 또는 다른 기술을 사용하는 많은 다른 프레임워크를 이용하여 사용 할 수 있습니다. 앞서 언급 한 바와 같이, SPA를 구축 할 때 서버에 가장 눈에 띄는 역할입니다.

데이터의 노출하는 것 이외에도 데이터 서비스는 주어진 애플리케이션에 의해 요구되는 보안을 제공 할 책임이 있습니다.

### 데이터 캐싱 Data Caching

일부 어플리케이션은 서버상에서 잦은 변경없는 데이터를 낭비합니다. 이 유형의 데이터(제품 번호, 국가, 주, 부서, 위치 등)는 종종 사용자간에 공유 될 수 있습니다. 데이터 저장소에 대한 쿼리가 최소화 되도록 서버는 캐싱 데이터에 중요합니다. Node.js, ASP.NET MVC, PHP, 등등 많은 다른 서버-사이드 프레임워크를 사용하는거에 상관없이 어플리케이션의 확장성을 크게 증가시키는 캐싱 기능에 보다 더 빠르게 액세스 할 수 있습니다.  그것은 SPA 및 다른 유형의 어플리케이션의 서버의 역할을 통해 언제나 노력하려고 생각합니다. 캐시는 최고 입니다!(적절하게 사용하는 경우)

 
### 동적 뷰 제공 Serving Dynamic Views

많은 SPA는 클라이언트 측에서 처리한 다음 서버에서 정적 HTML 뷰를 로드합니다. 예를 들어, AngularJS는  주어진 라우트가 처리 될 때 뷰가 런타임시 로드 될 수 있도록 뷰 경로와 연관 시킬 수 있습니다. 여기에 AngularJS를 사용하여 라우트와 뷰 (templateUrl 값) 정의의 예입니다 

    $routeProvider
        .when('/customers', {
            controller: 'CustomersController',
            templateUrl: '/app/views/customers/customers.html'
        });

정적 HTML 뷰가 많은 상황에서 작업하는 동안, 뷰 요청 중에 일부 데이터를 로드 데이터 뷰의 일부를 입력 한 다음 추가 처리를 위해 클라이언트로 내려 보낼 수있는 다른 시나리오가 있습니다 . While static HTML views work in many scenarios, there are other scenarios where you may want to load some of the data during the view request, fill in a part of the view with the data, and then send it down to the client for further processing. Why? Doing that can eliminate one or more HTTP calls from the browser to the server to retrieve data (via Ajax, web sockets, etc.). The route shown earlier may be changed to the following to allow for a dynamic view to be generated:

 

    $routeProvider
        .when('/customers', {
            controller: 'CustomersController',
            templateUrl: '/views/customers'
        });

 

True, this technique will cause the number of bytes sent from the server to the client to increase, but sometimes reducing the number of HTTP calls can result in a nice performance boost – especially when it comes to mobile devices.

While dynamically generating views and pre-populating them with some of the data certainly isn’t appropriate for every type of SPA out there, some SPAs may benefit from utilizing this type of server-side functionality. Some people may argue that this approach is against the true nature of SPAs but I would argue that every application is unique and there’s no such thing as one size fits all. Pre-filling SPA views with data on the server may be beneficial in some scenarios. Who says that you can’t create what I like to call “mixed mode SPAs” (MM-SPAs….OK I’ll admit that doesn’t exactly role off the tongue :-)) where the server does more than simply serve up data, scripts/styles, and static views?

 

### 뷰 캐싱 View Caching
In addition to data caching, the server may also be used to cache HTML views that are retrieved by a SPA. As mentioned earlier, views may be dynamically generated on the server, and in situations where data doesn’t change often and can be shared across users, the views and data may be cached by the server to allow them to be served in a more efficient and scalable manner.

Once views reach the client they can also be cached there of course for scenarios where a “fresh” view isn’t required each time a route is triggered.

 

### 보안과 동적 뷰 Security and Dynamic Views
Security is a key part of many applications. SPAs that load static HTML views from the server more than likely handle security on the client-side (you of course can’t rely on the client for any type of true security) as well as through the data service exposed by the server (where the real security checks should occur). What if your HTML view needs to load specific sections of a view dynamically based upon roles, claim sets, or other types of security constructs?

The server can once again be used to dynamically generate the view based upon specific security requirements. That way HTML fragments aren’t sent down to the client only to be hidden by the SPA framework based upon a user’s role (and easily unhidden by a power user using dev tools). Only the view content that the authenticated and authorized user should see based upon their current roles/permissions is sent down to the browser. I think this is definitely an area where mixed mode SPAs can be very appropriate depending upon the needs and requirements of the application.

 

 

### 보안, 보안, 보안 Security, Security, Security
I can’t emphasize enough how important the role of the server is when it comes to security. While you can certainly send down roles, permissions, and other security items to the client so that data or HTML fragments can be shown/hidden as appropriate in views, it’s critical that the server validates everything coming back to it.

Browser dev tools make it super easy to tweak HTML, CSS, and JavaScript so storing a user’s security roles on the client (as just one example) is fine but every request to the server should be validated on the server-side to ensure that the user really does have a given role/permission and can perform a specific action. Otherwise, a hacker can easily compromise your application and data by simply changing client-side variables. Using client-side code to secure applications (SPA or otherwise) is not a good way to go and arguably quite irresponsible.

### Validation
I normally consider validation to be part of the overall data service component mentioned above but it’s important enough to call it out separately. As with client-side security, client-side validation is a frail solution that can’t stand on its own. All validation of SPA data has to be validated on the server to ensure that the client-side code, and data haven’t been tampered with.

### 요약 Summary
Is this a complete list of all the ways a server can be used with SPAs? Of course not – this is simply a few things I’ve been thinking about as I’ve interacted with different companies building SPAs. If you have additional ways that you’re using the server with SPA applications leave a comment.

Single Page Applications (SPAs) are great and can provide a unique user experience when built properly. But, switching to SPAs doesn’t mean that all of your server-side skills have to be thrown out the window.
