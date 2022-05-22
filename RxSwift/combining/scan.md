# scan

- Observable에 의해 방출되는 각 항목에 순차적으로 함수를 적용하고 각 연속적인 값을 방출한다.
- reudce 함수와 비슷하지만, 순서대로의 값을 전부 출력해준다. 

<img width="744" alt="image" src="https://user-images.githubusercontent.com/96224311/169687620-4acb6547-4290-434d-bba3-a5e3f21fafd0.png">

```swift

let disposeBag = DisposeBag()

let source = Observable.of(1, 2, 3, 4, 5, 6)

source.scan(0, accumulator: +)
  .subscribe(onNext: { print($0) } // 1, 3, 6, 11, 17
  .disposed(by: self.disposeBag) 
