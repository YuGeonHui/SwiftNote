## network with throw
- 오류 처리는 네트워크와 가장 많이 사용된다.
- 네트워크에서 사용할 에러를 선언을 해놓으면 (Error 프로토콜 채택)

```swift
enum NetworkError: Error {
    case badURL
    case decodingError
    case badRequest
    case noData
    case custom(Error) // 사용자 지정 오류인 경우
}
```
- 네트워크 통신을 코드로 나타내면 아래와 같다.
- Result 타입은 success와 failure로 나타내지는 타입이다.
- try? 로 실행을 하는 이유는 오류가 발생할 경우, nil르 나타내주기 위해서 사용한다.
- nil로 나타내 주었기 때문에, if let을 통해 언래핑 하는 과정을 볼 수 있다.

```swift
struct Post: Decodable {
    let title: String
    let body: String
}

func getPosts(completion: @escaping (Result<[Post], NetworkError>) -> Void) {
    
    guard let url = URL(string: "https://jsonplaceholder.typicode.com/posts") else {
        completion(.failure(.badURL)) // URL이 잘 못 된 경우 출력되는 오류
        return
    }
    
    URLSession.shared.dataTask(with: url) { (data, response, error) in
    
        if let error = error {
            
            completion(.failure(.custom(error))) // 에러가 존재하는 경우
            
        } else if (response as? HTTPURLResponse)?.statusCode != 200 {
            
            completion(.failure(.badRequest)) // statusCode가 200이 아닌 경우
            
        } else {
            
            // 정상 케이스 인경우
            guard let data = data else {
                completion(.failure(.noData)) // 데이터가 존재하지 않는 경우
                return
            }
            
            let posts = try? JSONDecoder().decode([Post].self, from: data) // nil을 출력하기 위해 try?로 나타낸다.
            if let posts = posts {
                
                completion(.success(posts))
                
            } else {
                completion(.failure(.decodingError))
            }
        }
        
    }.resume()
    
}
```
- 위의 코드를 실행을 해보면 아래와 같다.
- 오류가 발생한 경우 failure 부분에서 해당되는 에러를 출력해준다.
```swift
getPosts { (result) in
    switch result {
        case .success(let posts):
            print(posts)
        case .failure(let error):
            print(error)
    }
}
```
