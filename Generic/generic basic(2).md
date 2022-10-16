## generic에 대해서 더 알아보자 

- 아래와 같은 3가지의 배열이 존재할 때 

```swift 
struct Movie: Equatable {
    let name: String
}

let numbers = [1,2,3,5,6,7,10]
let names = ["Alex", "John", "Mary", "Steve"]
let movies = [Movie(name: "Batman"), Movie(name: "Spiderman"), Movie(name: "Superman")]
```

- 해당 값이 존재하면, 해당 값의 인덱스를 추출하는 함수를 만들어 보자

```swift 
func findIndex<T: Equatable>(from list: [T], valueToFind: T) -> Int? {
    
    return list.firstIndex { (item) -> Bool in
        return item == valueToFind // Equatable을 준수하지 않기 때문에 오류발생!
    }
}
```
- 제너릭 타입을 통해 만들었지만, Equatable을 준수하지 않았기 때문에 오류가 발생한다.
- 이를 해당하기 위해 아래와 같이 함수를 변경해준다.

```swift 
func findIndex<T: Equatable>(from list: [T], valueToFind: T) -> Int? {
    
    return list.firstIndex { (item) -> Bool in
        return item == valueToFind
    }
}

print(findIndex(from: numbers, valueToFind: 2))
print(findIndex(from: names, valueToFind: "Alex"))

let batmanMovie = Movie(name: "Batman")

print(findIndex(from: movies, valueToFind: batmanMovie))
```
- 하지만 무비 객체를 비교하는 경우 오류가 밣생한다.
- 이를 해결하기 위해서는 Movie 구조체가 Equatable을 준수하면 에러가 해결된다 .

```swift 
struct Movie: Equatable {
    let name: String
}
```
- 이러면 3가지 타입 모두 findIndex() 함수를 사용할 수 있다.
