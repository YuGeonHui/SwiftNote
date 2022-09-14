# FetchMethod 

> Network 작업 담당 객체를(Service) 만든다.
> 해당객체를 NetworkService라고 할때, 객체를 사용하여 네트워크 작업 진행

```swift 
enum NetworkError: Error {
    case invalidRequest
    case transportError(Error)
    case resonseError(statusCode: Int)
    case noData
    case decoidngError(Error)
}

final class NetworkService {
    
    let session: URLSession
    
    init(configuration: URLSessionConfiguration) {
        session = URLSession(configuration: configuration)
    }
    
    func fetchProfile(userName: String, completion: @escaping (Result<GithubProfile, Error>) -> Void) {
        
        let url = URL(string: "https://api.github.com/users/\(userName)")!

        let task = session.dataTask(with: url) { data, response, error  in
            
            if let error = error {
                completion(.failure(NetworkError.transportError(error)))
                return
            }
            
            if let httpResponse = response as? HTTPURLResponse, !(200..<300).contains(httpResponse.statusCode) {
                completion(.failure(NetworkError.resonseError(statusCode: httpResponse.statusCode)))
                return
            }
            
            guard let data = data else {
                completion(.failure(NetworkError.noData))
                return
            }

            do {
                
                let decoder = JSONDecoder()
                let profile = try decoder.decode(GithubProfile.self, from: data)
                
                completion(.success(profile))
                
            } catch let error as NSError {
                
                completion(.failure(NetworkError.decoidngError(error)))
            }
        }
        task.resume()
    }
}



let networkService = NetworkService(configuration: .default)

networkService.fetchProfile(userName: "YuGeonHui") { result in
    switch result {
    case .success(let profile):
        print("Profile: \(profile)")
    case .failure(let error):
        print("Error: \(error)")
    }
}
```
