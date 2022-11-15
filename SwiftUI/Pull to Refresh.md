## Pull to Refresh

- SwiftUI에서는 (iOS 15 이상)에서는 당겨서 새로고침을 지원한다.
- refreshable을 통해 사용이 가능하다.
- 아래와 같은 ViewModel이 존재한다고 가정해보자

```swift 
import Foundation

class PullToRefreshViewModel: ObservableObject {
    
    @Published var customers: [String] = []
    
    func fetch() {
        
        let letters = "abcdefghi"
        var names: [String] = []
        
        DispatchQueue.main.asyncAfter(deadline: .now() + 2) {
            
            for _ in 1...20 {
                
                let randomName = String((0...letters.count).map { _ in letters.randomElement()! })
                names.append(randomName)
            }
            
            self.customers = names
        }
    }
}
```
- 해당 뷰모델은 2초마다 새로운 이름을 생성해서 customer의 배열에 넣어주는 역할을 한다.
- 이 역할을 메인뷰에서 불러보면 아래와 같다.

```swift 

import SwiftUI

struct PullToRefreshView: View {
    
    @StateObject private var viewModel = PullToRefreshViewModel()
    
    var body: some View {
       
        List(viewModel.customers, id: \.self) { customer in
            Text(customer)
        }.onAppear {
            viewModel.fetch()
        }.refreshable {
            viewModel.fetch()
        }
    }
}
```
- refreshable을 통해 Pull to Refresh를 구현 할 수 있다.
- 리스트 뷰를 아래와 드래그 하면 해당기능이 실행됨을 볼 수 있다.
