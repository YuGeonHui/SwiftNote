# Keyboard

> FirstResponder란?
> UIWindow 객체란 사용자에 가장 가까이 위치한 객체이다.
> 사용자로부터 발생하는 터치 관련 이벤트를 내부 객체로 전달하는 역할을 담당한다.

## FirstResponder
- TextView에서 클릭을 하면 FirstResponder로 지정이된다.
- FirstResponder을 지정하는 방법은, ```becomeFirstResponder```을 통해서 지정한다.
- FirstResponder을 해제하는 방법은, ```resignFirstResponder```을 통해서 지정한다.

## KeyboardType
- ```UIKeyboardType```의 enum타입을 따른다.
- numberPad, PhonePad 등 다양한 값을, 상황에 맞춰 사용하면 된다.

## KeyboardAppearance
- 일반적으로는 default 값을 사용한다. (light, dark 모드도 사용 가능)
- 일반적으로 KeyboardAppearance를 설정하는 경우는 디자인이 정해져 있는 경우 (색 맞춤)

## ReturnType 
- ReturnType은 스페이스바 옆에 있는 모양을 ReturnType이라고 한다.
- Return 타입은 ```returnType``` 속성을 통해 설정이 가능하다.
- next, go, google등 다양한 방법이 존재한다.

## KeyboardNotification 
- KeyboardNotification을 사용하여, keyboard의 관련된 Noti를 전달할 수 있다.
- ex) 텍스트 필드 내부에서 글자가 길어질 때, 키보드 높이만큼 inset적용
