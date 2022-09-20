## 코디네이터는 ViewController의 책임을 면제 해 주므로 훌륭한 도구입니다.

단일 책임 원칙을 준수하도록 도와줌으로써 ViewController를 훨씬 더 가볍고 쉽게 재사용 할 수 있도록합니다.

ViewController는 그 전에 어떤 ViewController가 왔는지,

어떤 것이 다음에 올지 또는 어떤 종속성이 전달되어야 하는지를 알지 못합니다. 자신의 화면과 관련된 레이아웃, 비지니스 로직만 처리하고 있죠.

## 적절한 처리를 위해 ViewController의 탐색과 관련된 모든 작업을 코디네이터 에게 보내야합니다.

## Navigation 처리는 코드 전체에 흩어져있지 않게 됩니다. (코디네이터의 구현체 안에 있게 될 것 입니다.)

# 기본적으로 코디네이터는 다음의 기능을 수행해야 합니다.

1. ViewController, ViewModel, Reactor .. 등의 화면단위에 사용하는 클래스의 인스턴스화합니다.
2. ViewController 및 ViewModel, Reactor .. 등에 종속성을 주입해야될 인스턴스에 삽입합니다.
3. ViewController를 화면에 표시하거나 Push합니다.
