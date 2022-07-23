# TextDelegate의 흐름
- TextField, TextView를 Tap하게 되면 두개의 뷰 전부 First Responder로 변경된다.
- (편집모드로 전환) 해당 시점에, 키보드가 표시되게 된다.

### ```TextFieldShouldBeginEditing(_:)```, ```textviewShouldBeginEditing```
- 해당 View를 최초로 tap한 경우 실행되는 메서드이다.

### ```textFieldDidBeginEditing```, ```textViewDidBeginEditing```
- 편집 모드가 실행된 경우 호출한다.

### ```textField(_: shouldChangeCharactersIn:replacementString:)```
- 삭제버튼 (x)를 클릭한 경우 : ```textFieldShouldClear(_:)```
- Retun키를 입력한 경우 : ```textFieldShouldReturn(_:)```

### ```textView(_:shouldChangeTextIn:replacentText:)```
- true를 return하는 경우 ```textViewDidChange(_:)```를 호출한다. 
- 특정범위를 선택하거나, 입력 포커스를 이동한 경우 : ```textViewDidChangeSelection(_:)```을 호출한다.
- Attachment로 이미지를 삽입하거나, 링크등을 선택한 경우 : ```textView(_:shouldInteractWith:in:interaction:)```을 호출한다.

### ```TextFieldShouldEndEditing(_:)```, ```textViewShouldEndEditing```
- 편집이 종료되는 시점(포커스를 이동하거나, 다른 화면으로 이동한 경우)
- true를 return한 경우 키보드는 화면에서 사라지며, 편집은 종료가 된다.

### ```TextFieldDidEndEditing(_:)```, ```textViewDidEndEditing```
- 편집 모드가 완전히 종료된 경우 호출한다.
