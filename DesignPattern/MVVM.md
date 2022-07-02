# 🤔 왜 MVVM이 생겼나?

### 기존 MVC 패턴의 문제

- 애플에서 가이드 하던 MVC 패턴
    
    ![mvvm1_16d8161.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9c3198a2-cea6-44d0-a946-7ed8da6c1b70/mvvm1_16d8161.png)
    
- `view` `view controller`  이 둘은 View 와 Controller 레이어로 나누어서 설명은 했지만,
- 실제로 구현을 할때는 이둘은 거의 분리되지 않음
    
    ![intermediate_5287a0c.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b4ee004b-8a67-4fb8-bff4-97efbeca9478/intermediate_5287a0c.png)
    
- 따라서, 위와 그림과 같이 표현되는게 좀 더 현실모습을 잘 담고 있음
- 이러다 보니, `View Controller` 에 많은 로직들이 존재하게됨
    - 프레젠테이션 로직
    - 비즈니스 로직
    - 데이터 접근 로직
    - 등등..
- 결국에 **M**assive **V**iew**C**ontroller 라는 불명예 스러운 용어가 따라 붙게됨

### 위와 같은 이슈로 발생하는 문제

- `View Controller`  가 너무 많은 책임을 지고 있음
- 모델(데이터)를 직접 접근하면서 수정하다보니, 버그에 취약하게 됨
- 유지보수가 어려움 (변경과 수정에 어려움이 많아짐)

# 🤔 기존 문제를 어떻게 해결할까?

- `ViewController` 를 View 레이어로 생각하자
    - View 레이어에서 해야하는 일
        - 데이터를 뷰에 표시
        - 사용자 인터랙션 받기
- View 레이어에 알맞은 형태로 Model 을 가공해서 전달하자
    - 즉, ViewModel 을 제공하자
        - 예를 들어 Model 에 `Date` 타입이 있다면, `String` 으로 변환해서 주자
    - ViewModel 에 필요한 각종 Controller 및 Manager 는 View 레이어가 모르게 하자
        - 예를 들어, `ViewController`  에 네트워크서비스, 디비접근 리포지토리 등을 놓지 말자
- 결론적으로 `ViewModel` 을 만들자

# 🤔 MVVM 은 그럼 어떻게 만드냐?

- MVVM 약자?
    - Model - View - ViewModel
- MVVM 구조
    
    ![mvvm_b27768d.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/791ba970-cd25-4358-a0ea-39147c82ef77/mvvm_b27768d.png)
    
- ViewController 는 ViewModel 을 들고 있음
- ViewModel 은 Model(Data) 을 들고 있음
- ViewModel 은 아래의 역할을 함
    
    ### 1. Data → Output
    
    - Model(Data) 를 가지고 있고,
        - View 에 적용할수 있도록 가공되어 있음
    
    ### 2. User Action → Input
    
    - User Action 에 대한 처리를 담당함
        - 실제 액션에 대해서는 View 가 알려줌
        - 다만 액션으로 수행되어야 하는 비즈니스 로직을 처리함
