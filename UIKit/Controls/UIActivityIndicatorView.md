# UIActivityIndicatorView
- 진행 상황을 나타내주는 View이다.
- 진행상황을 알고 있는경우 ProgressView를 사용하고, 아닌경우 해당뷰를 사용한다.
- 사이즈는 medium, large가 존재한다. 

## isAnimating
- 현재 Activity뷰가 실행 여뷰를 알 수 있다. (Bool)

## hidesWhenStopped
- 완료 되었을 때, 해당 View를 숨김 여뷰를 결정한다. (Bool)

## 애니메이션 Control방법
- startAnimation() : 진행을 시작하기 위한 메서드
- stopAnimating() : 진행을 중지하기 위한 메서드 
