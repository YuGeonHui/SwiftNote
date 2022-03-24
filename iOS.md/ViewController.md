# ViewController LifeCycle

1. ViewDidLoad() : 기본 아울렛, 액션 설정 
2. ViewWillAppear() : 실제로 화면이 표출되기 직전 
3. ViewDidAppear() : 타이머 시작, 카운트 다운 등 하기 좋음 
4. ViewWillDisappear() : 애니메이션을 중지하고, 모양을 변경하고 싶을 때 
5. viewDidDisappear(): 이전 보기에 대해 무엇인든 변경할 수 있는 마지막 순간 
