## Optional Unwrapping 

- 스위프트에서 옵셔널을 Unwrapping 하는 방법을 알아보자.

```swift
struct Student {
    let firstName: String
    let lastName: String
    var middleName: String?
    var grade: String?
}

var student = Student(firstName: "John", lastName: "Doe")
student.middleName = "Johnson"
student.grade = "A"
```
- 다음과 같은 Student 구조체가 있을 때 (middleName, grade가 Optional인 구조체)
- 다음과 같은 구조체를 student로 인스턴스 한 후, middleName과 grade의 값을 넣어줬다.

## if-let을 이용한 Optional Wrapping

```swift 
if let middleName = student.middleName, let grade = student.grade {
    print(middleName) // Johnson
    print(grade) // A
} 
```

- 만일 Unwrapping 한 값이 필요 없을 경우에는, 아래 처럼 사용하면 된다. (와일드 카드)

```swift
if let _ = student.grade {
    print("Student has been graded")
}
```

## guard let을 통한 Optional Unwrapping

```swift 
func displayStudent(student: Student) {
    
    guard let middleName = student.middleName,
          let grade = student.grade else {
        return
    }
    
    print(middleName, grade)
}

displayStudent(student: student) // Johnson A
```
- guard let을 사용하는 경우에는 문구 밖에서 Unwrapping한 값을 사용할 수 있다.
