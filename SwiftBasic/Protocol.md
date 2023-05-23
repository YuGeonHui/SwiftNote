# Protocol

1. 프로토콜은 데이터 타입으로 사용이 가능하다. (해당 프로토콜을 채택한 경우 사용가능)
2. 구조체에서도 프로토콜 사용이 가능하다. 
3. 프로토콜 내부에서는 구현하지 않는다.
4. 프로토콜을 채택하면 내부에서 프로토콜 내부의 것들을 구현해야만 한다. 
5. 상속과 프로토콜을 동시에 사용해야 하는 경우 -> 상속이후 프로콜을을 선언하면 된다.
6. Swift에서 Delegate Pattern을 작동하게 만드는 기술이다. 

```swift
protocol AdvancedLifeSupport {
  func performCPR() 
}

class EmergencyCallHandler {
  var delegate: AdvancedLifeSupport?
  
  func assessSituation() {
    print("Can you tell me what happend?")
  }
  
  func medicalEmergency() {
    delegate?.performCPR() // 어떤 delegate인지 신경 쓰지 않는다. 
  }
}

Struct Paramedic: AdvancedLifeSupport {
  
  init(handler: EmergencyCallHandler) {
    handler.delegate = self
   }
  
  func performCPR() {
    print("The paramedic does chest compressions, 30 per seconds.")
  }
}

class Doctor: AdvancedLifeSupport {

  init(handler: EmergencyCallHandler) {
    handler.delegate = self
  }

  func performCPR() {
    print("The paramedic does chest compressions, 30 per seconds.")
  }

  func useStethescope() {
    print("Listening for heart sounds")
  }
}

class Surgeon: Doctor {

  override func performCPR() {
    super.performCPR()
    print("Sings statying alive by the BeeGees")
  }
  
  func useElectricDrill() {
    print("Whirr...")
  }
}

let emilio = EmergencyCallHandler()
// let pete = Paramedic(handler: emilio)
let angela = Surgeon(handler: emilio)

emilio.assessSituation()
emilio.medicalEmergency()
```

# 프로토콜 개념 추가
- 프로토콜은 1급 객체이다. (타입으로 사용이 가능)
- 프로토콜에서는 최소한의 것만 구현 하면된다. (함수의 헤더, 변수)
- 프로토콜의 확장을 통해 구현하는 경우 기본구현으로 적용 가능하다. (반복적으로 같은 코드를 작성해야 하는경우)
