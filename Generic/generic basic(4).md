## generic

- 제너릭 형식으로 제너릭 타입을 만들 수 있다.
- 제너릭을 기존 유형에 사용할 수 있을 뿐만 아니라, 아예 새로운 제너릭 타입으로 만들 수 있다.
```swift 
import UIKit

enum NetworkError: Error {
    case badUrl
}

struct Post: Codable {
    let title: String
}

enum Callback<T: Codable, K: Error> {
    case success(T)
    case failure(K)
}

func getPosts(completion: (Callback<[Post], NetworkError>) -> Void) {
    
    // get all posts
    let posts = [Post(title: "Hello World"), Post(title: "Introduction to Swift")]
    completion(.success(posts))
    //completion(.failure(.badUrl))
    
}

getPosts { (result) in
    switch result {
        case .success(let posts):
            print(posts)
        case .failure(let error):
            print(error)
    }
}
```
