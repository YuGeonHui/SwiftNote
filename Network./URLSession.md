# URLSession

```swift
import Foundation

// configuration -> urlsession -> urlsessionTask

let configuration = URLSessionConfiguration.default
let session = URLSession(configuration: configuration)

let url = URL(string: "https://api.github.com/users/YuGeonHui")!

// data : 요청한 데이터
// response : 응답 값 (서버로부터)
// error : 에러
let task = session.dataTask(with: url) { data, response, error in
    
    guard let httpResponse = response as? HTTPURLResponse, (200..<300).contains(httpResponse.statusCode) else {
        
        debugPrint("response: \(response)")
        return
    }
    
    guard let data = data else { return }

    let result = String(data: data, encoding: .utf8)
    print(result)
}

task.resume()
```
