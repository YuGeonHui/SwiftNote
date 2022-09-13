# Data Decoding

> 서버에서 들어온 값을 앱 내에서 사용할 수록 있도록 반환하는 과정

- App Model -> Json : Encoding
- Json -> App Model : Decoding

```swift
struct GithubProfile: Codable {
    
    let login: String
    let avatarUrl: String
    let htmlUrl: String
    let followers: Int
    let following: Int
    
    enum CodingKeys: String, CodingKey {
        
        case login
        case avatarUrl = "avatar_url"
        case htmlUrl = "html_url"
        case followers
        case following
    }
}

let configuration = URLSessionConfiguration.default
let session = URLSession(configuration: configuration)

let url = URL(string: "https://api.github.com/users/YuGeonHui")!

let task = session.dataTask(with: url) { data, response, error  in
    
    guard let httpResponse = response as? HTTPURLResponse, (200..<300).contains(httpResponse.statusCode) else {
        print("response: \(response)")
        return
    }
    
    guard let data = data else { return }
    // data -> GithubProfile

    do {
        
        let decoder = JSONDecoder()
        let profile = try decoder.decode(GithubProfile.self, from: data)
        
        print("profile: \(profile)")
        
    } catch let error as NSError {
        
        print("error: \(error.localizedDescription)")
    }
}

task.resume()

```
