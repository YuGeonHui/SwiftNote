## try!와 try?
- ```try?``` : 에러 발생 시 nil을 반환합니다.
- 에러가 발생하지 않으면 반환 타입은 옵셔널 이며, 반환 타입이 없이도 사용 가능하다.
- do-catch문을 사용하지 않아도 오류가 발생가능 한 함수를 실행 할 수 있다.

- ```try!``` : 에러 발생 시, crash가 발생합니다.
- 에러가 발생하지 않는 걸 보장하고 사용해야 한다. (반환 타입은 언래핑)

```swift
struct Email {
    let text: String
    
    init(_ text: String) throws {
        
        guard !text.isEmpty else {
            throw ValidationError.noEmptyValueAllowed
        }
        
        let pattern = "[A-Z0-9a-z._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,64}"
        let emailPredicate = NSPredicate(format: "SELF MATCHES %@", pattern)
        
        let isValid = emailPredicate.evaluate(with: text)
        if isValid {
            self.text = text
        } else {
            throw ValidationError.invalidEmail
        }
    }
}

// do-catch를 사용한 오류 구문 실행
do {
    let email = try Email("johndoe@gmail.com")
    print(email)
} catch {
    print(error)
}

// try!를 사용한 오류 구문 실행
let email = try! Email("johndoe@gmail.com")
print(email)
```

