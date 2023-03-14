# MVP란?
모델-뷰-프리젠터(model-view-presenter, MVP)는 모델-뷰-컨트롤러(MVC) 아키텍처 패턴의 파생 패턴으로,사용자 인터페이스를 개발하기 위해 대부분 사용된다.

MVP에서 프리젠터는 "middle-man"의 기능을 담당한다. MVP에서는 모든 프레젠테이션 로직은 프리젠터로 넘어간다,
`출처 - 위키피디아`

MVC 패턴과 유사하지만, MVC의 Controller의 역할을 Presenter가 해준다고 볼 수 있다.
![](https://velog.velcdn.com/images/zzckckck3/post/a9258f93-200c-4032-bac1-81411c1eb47b/image.png)


# Presenter?
그럼 그냥 MVC를 쓰면 되는데 왜 MVP를 쓰냐 하면, MVC패턴에서는 Model이 View를 업데이트 하기에, 서로 연결이 되어있어 의존관계를 갖게 된다. 하지만 MVP는 Model과 View를 완전분리시켜 오직 Presenter를 통해서면 상태나 변화를 알려줄 수 있도록 설계한다.

# 구성
### Model
- 프로그램 내부적으로 쓰이는 데이터를 저장하고, 처리하는 역할(비즈니스 로직)
- View또는 Presenter등 다른 어떤 요소에도 의존적이지 않은 독립적인 영역

### View
- UI를 담당하며 안드로이드에서는 Activity, Fregment를 예시로 들 수 있다.
- Model에서 처리된 데이터를 Presenter를 통해 전달받아서 유저에게 보여줌.
- 유저의 행동 및 상태변화를 주시하며 Presenter에게 전달
- Presenter를 이용해 전달받기에, Presenter에 상당히 의존적이다.

### Presenter
- Model과 View사이의 매개체
- 전체적으로는 Controller와 유사하지만, View와 **인터페이스**를 통해 상호작용한다
- 인터페이스를 통해 상호작용 하므로 MVC가 가진 테스트 문제와 함께 모듈화/유연성 문제 역시 해결 가능
- View에게 표시할 데이터만 전달하며 어떻게 표시할지는 View에서 처리

# 동작
![](https://velog.velcdn.com/images/zzckckck3/post/df4e9f25-1ee1-4c0e-901e-35aaf8df083e/image.png)
>
- 모든 입력(Input)들은 View로 전달된다.
- Presenter는 입력에 해당하는 Model을 업데이트 한다.
- Model 업데이트 결과를 기반으로 View를 업데이트 한다.
- Presenter는 해당 View를 참조한다.(View와 Presenter는 1:1 관계)
- Presenter는 View와 Model 인스턴스를 가지고, Model과 View 사이의 매개체 역할을 한다.

# 장점
- MVC보다 코드가 깔끔해지기에 유지보수가 쉬워진다.
- Model과 View의 결합도를 상당히 낮출 수 있기 때문에 기능 추가 및 변경 시에 원할해진다.
- UI, Data파트를 나누어서 분업이 더욱 쉬워진다.

# 단점
- 프로그램이 무거워질수록 View와 Presenter사이의 의존성이 더 강해지기에 상당히 큰 프로젝트의 경우 유지보수가 더 어려워질 수 있다.
