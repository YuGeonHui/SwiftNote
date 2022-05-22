# Reduce 

- Reduce 연산자는 Source Observable에서 방출된 첫 번째 항목에 함수를 적용한 다음 Source Observable에서 방출된 두 번째 항목과 함께 함수의 결과를 함수에 다시 공급한다.

<img width="747" alt="image" src="https://user-images.githubusercontent.com/96224311/169687521-23842861-0ebc-46c5-a8f8-1ad80190cd49.png">


```swift

let disposeBag = DisposeBag()

let source = Observable.of(1, 2, 3)

source.reduce(0, accumulator: +)
  .subscribe(onNext: { print($0) }
  .disposed(by: self.disposeBag) // 6
  
source.reduce(0, accumulator: { summary, newValue in 
  return sumary + newValue 
  })
  .subscribe(onNext: { print($0) }
  .disposed(by: self.disposeBag) // 6

```  
  
