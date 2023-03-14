# MVVM이란?
모델-뷰-뷰 모델(model-view-viewmodel, MVVM)은 하나의 소프트웨어 아키텍처 패턴으로-마크업 언어 또는 GUI 코드로 구현하는-그래픽 사용자 인터페이스(뷰)의 개발을 비즈니스 로직 또는 백-엔드 로직(모델)로부터 분리시켜서 뷰가 어느 특정한 모델 플랫폼에 종속되지 않도록 해준다. MVVM의 뷰 모델은 값 변환기인데, 이는 뷰 모델이 모델에 있는 데이터 객체를 노출(변환)하는 책임을 지기 때문에 객체를 관리하고 표현하기가 쉬워진다는 것을 의미한다. 이러한 점에서, 뷰 모델은 뷰 보다는 더 모델인 것이며, 모든 뷰들의 디스플레이 로직을 제외한 대부분의 것들을 처리한다. 뷰 모델은 '백-엔드 로직에 대한 접근'과 그 주변부의 '뷰에서 지원하는 유즈 케이스 집합'으로 구성되도록, 중재자 패턴으로 구현할 수도 있다.
`출처 - 위키피디아`

MVVM역시 MVC와 비슷하지만, Contoller의 역할을 View Model이 처리한다.


# View Model?
뷰 모델은 공용 속성과 공용 명령을 노출하는 뷰에 대한 추상화이다. MVC의 Controller, MVP의 Presenter를 대신하여 Binder(View Model에서 사용)를 가지고 있는데, 이는 뷰 모델에 있는 뷰에 연결된 속성과 뷰 사이의 통신을 **자동화**해준다. 이를 구현하기 위해서는 [상용구 코드(boilerplate code)](https://ko.wikipedia.org/wiki/%EC%83%81%EC%9A%A9%EA%B5%AC_%EC%BD%94%EB%93%9C)의 자동 생성이 필수이다.

# 동작
![](https://velog.velcdn.com/images/zzckckck3/post/8a9c69ac-e155-4941-b44f-676fc66fc99d/image.png)
>
- 사용자의 Action들은 View를 통해 들어온다.
- View에 Action이 들어오면 ViewModel에 Action을 전달한다.
- ViewModel은 Model에게 데이터를 요청한다.
- Model은 ViewModel에게 요청받은 데이터를 응답한다.
- ViewModel은 응답 받은 데이터를 가공하여 저장한다.
- View는 Data Binding을 이용해 UI를 갱신시킨다.

# 장점
MVC, MVP가 가지는 단점을 해결할 수 있다. 즉, 의존성을 거의 완벽하게 제거할 수 있다.

# 단점
효율성에 비해 설계가 너무 힘들다는 점이 있다.
