# 리스트 및 그리드 그리는 방밥 (Advanced)

![image](https://user-images.githubusercontent.com/96224311/172143539-1c0e593a-e7f2-4a0e-985f-b0c9d948a1aa.png)
![image](https://user-images.githubusercontent.com/96224311/172026267-60a1c22d-fda0-4958-b2b9-7b5332475872.png)
![image](https://user-images.githubusercontent.com/96224311/172143883-554aaf33-7c77-40a7-8c55-1941b72c1b3f.png)

- 기존구현은 간단하고 유연하다.
- 보통 Controller가 데이터를 받아와서, UI에게 변경을 알림
- 점점 복잡한 구현이 생기면서, 기존방식 사용 시 이슈가 발생
- Controller가, UI를 들고 있는 데이터 사이에서 일치하지 않음 
> 앱에서는 어느것이 맞는 데이터인지 판단하게 어렵다.


# Single Source Of Truth Data의 필요성 증가 
- 기존의 구현 방식에서 어떤 데이터(Controller, UI가 각각 데이터를 들고 있음)가 참인지 알기 어려웠다.
- 따라서, 근본적인 문제 해결방식은 참인 데이터를 한개만 두도록 한다. -> Single Source of Truth 
- 그렇게 제안된 방법이 Diffable Datasource 
![image](https://user-images.githubusercontent.com/96224311/172144390-0544103f-6cc0-4f72-a12b-4986bfb63786.png)

# SnapShot의 도입 
- 한가지 참인 데이터를 관리하는 객체 
- IndexPath를 쓰지 않고, 색션 및 아이템에 대해서 Unique ID를 사용함 
> Unique + Hashable 
```swift
struct MyModel: Hashable {
  let identifier = UUID()
  func hash(into hasher: inout Hasher) {
    hasher.combine(indentifier)
   }
   
   static func == (lhs: MyModel, rhs: MyModel) -> Bool {
    return lhs.identifier == rhs.identifier 
   }
```
