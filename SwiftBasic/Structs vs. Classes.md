# Structs vs. Claseses

## Apple은 항상 기본적으로 구조체를 생성할 것을 권장한다. 

1. 구조체는 상속이 불가능 하지만, 클래스는 상속이 가능하다.
2. 클래스는 init()을 호출해줘야 한다. 
3. 클래스는 참조형태 값으로 저장(let) / 구조체는 복사본 생성 (var)
5. 내부에서 값을 변경할 때, struct는 mutating 키워드가 필요하다.
6. 구조체는 값으로 전달된다. 
7. 구조체는 Referencing Count가 증가하지 않고, 클래스는 증가한다.

```swift
struct StructName {
   property
   method
   initializer
   subscript
}

class ClassName {
   property
   method
   initializer
   deinitializer
   subscript
}
```
