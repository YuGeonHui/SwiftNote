# concat 

- 여러 옵저버블에서 방출하는 값들을 순서대로 방출해준다. 
- Concat은 이전 Observable이 완료될 때까지 사용자가 전달한 각 추가 Observable을 구독하기 위해 대기한다. 
- concat은 이전의 모든 옵서버블이 완료되기 전에 방출하는 항목을 볼 수 없으므로 Hot Observable이다.

<img width="743" alt="image" src="https://user-images.githubusercontent.com/96224311/169683011-b78f8f77-2a3d-4a37-894c-967af44f2326.png">

```swift
let disposeBag = DisposeBag()

let first = Observable.of(1, 2, 3)
let second = Observable.of(4, 5, 6)

let observable = Observable.concat([first, second])

observable.subscribe(onNext: { 
  print($0) // 1, 2, 3, 4, 5, 6
}).disposed(by: self.disposeBag)
```
