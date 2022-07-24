# UIStepper
- 값을 증가 또는 감소하기 위한 컨트롤입니다.
- 초기 값, 최대 값, 최소 값이 존재한다.
- 버튼을 누르면 속도가 점점 빨라지면서 증가 혹은 감소한다.

## UIStepper Property
- autorepeat : Stepper의 값을 누르고 있을 때, 계속 이벤트를 방출할지 여부 (Bool)
- isContinuous : 계속이벤트를 받을지, 마지막 이벤트만 받을지 결정 (Bool)
- wraps : Stepper의 값의 최대 값을 넘어간 경우 초기값으로 복귀해주는 속성 (Bool)
