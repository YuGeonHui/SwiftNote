## lazy 속성을 사용하여 문제를 해결하고 새로운 문제를 만나보자 

### lazy란 무엇일까 ??! 
- lazy는 인스턴스를 생성하는 시점에 값을 부여하고 싶지 않은 변수에 대하여 붙여주는 키워드입니다.
- 해당 프로퍼티가 처음 사용되기 전까지는 메모리에 올라가지 않는 의미이다.
- lazy라는 키워드가 붙으면 초기 값을 주지 않고, 첫 번째 호출 때 초기화를 해주겠다는 의미이기 때문에 변수만 가능하다. (var)


```swift
enum Level {
    case easy
    case medium
    case hard
}

struct Exam {
    
    var level: Level
    
    var questions: [String] {
        
        sleep(5) // 통신을 통해 가져온다고 가정한다.
        
        switch level {
            case .easy:
                return ["What is 1+2", "What is 1+2", "What is 2+2"]
            case .medium:
                return ["What is 11+22", "What is 11+22", "What is 32+42"]
            case .hard:
                return ["What is 122+332", "What is 441+255", "What is 266+250"]
        }
    }
}

var exam = Exam(level: .easy)
print(exam.questions)
print("wait for 1 second")
sleep(1)
print(exam.questions)
```

## 해당 코드를 실행해보자!
1. Exam 객체가 먼저 생성 될 것이다.
2. 객체가 생성된뒤 print(exam.questions)이 실행된다. 
3. questions 변수 내부에 sleep(5)가 존재하여 5초 뒤에 2번 프린트문이 실행될 것이다.
4. print("wait for 1 second") 실행되고, 1초 뒤에 print(exam.questions)이 실행될것이다.
5. 하지만!! 여기서 1초 뒤가 아닌 다시 5초뒤에 questions이 생성된다. 

> 이를 해결하려면 어떻게 해야될까 ?!?! 

```swift 
struct Exam {

    var level: Level

    private(set) lazy var questions: [String] = {

        sleep(5) // 통신을 통해 가져온다고 가정한다.

        switch level {
            case .easy:
                return ["What is 1+2", "What is 1+2", "What is 2+2"]
            case .medium:
                return ["What is 11+22", "What is 11+22", "What is 32+42"]
            case .hard:
                return ["What is 122+332", "What is 441+255", "What is 266+250"]
        }
    }()
}
```
- questions프로퍼티를 lazy로 선언하여, 인스턴스가 생성하는 시점에 값을 부여한다.
- 하지만 이 방법에도 문제가 존재한다. 

```swift
var exam = Exam(level: .easy)
print(exam.questions) 
var hardExam = exam
hardExam.level = .hard

print("[Hard Exam]")
print(hardExam.questions)
```
- 위와 같은 결과를 보면, print("[Hard Exam]") 이후에도 return값이 변경되지 않는다. (easy 문제와 동일)
- print(exam.questions) 에서 메모리 올렸기 때문에, 그 이후의 값을 바꿔줘도 올라가지 않는다 .
- 해당 문제를 해결하기 위해서는 print(exam.questions) 실행하면 hard와 관련된 문제가 나타난다.



