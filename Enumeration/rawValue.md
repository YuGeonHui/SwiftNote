## rawValue

- enum의 rawValue를 통해 값을 전달하는 경우, 다른 사용자에 의해 실수가 나올 수 있다.
- getWeather 함수를 통해 통신을 시도하는데, 이때의 unit값을 TemperatureUnit의 rawValue로 전달하고 있다.

```swift 
enum NetworkError: Error {
    case badURL
    case decodingError
}

enum TemperatureUnit: String {
    case imperial = "fahrenheit"
    case metric = "celsius"
}

func getWeather(unit: TemperatureUnit) throws {
    
    guard let weatherURL = URL(string: "www.weather.com/?unit=\(unit.rawValue)") else {
        throw NetworkError.badURL
    }
    
    print(weatherURL)
    
    // code to call the weather API
    
}

do {
    try getWeather(unit: .metric)
} catch {
    print(error)
}
```
- 만일 누군가가 TemperatureUnit의 rawValue값을 바꾼다면, 해당 함수에도 side Effect가 발생할 것이다. 
- 아래와 같이 TemperatureUnit의 rawValue의 값을 "F", "C" 로 바꾼다면 문제가 발생할 것이다.
- 위의코드에서 getWeather 함수에서 우리는 오류를 받게 될것이다. (API 주소의 변경으로 인한) 
 
```swift

enum TemperatureUnit: String {
    case imperial = "F"
    case metric = "C"
}
```

- 이러한 오류를 제거하기 위해서, 아래와 같이 리팩토링 하여 사용하면 좋다.
- getWeatherURL이라는 함수를 통하여, 각각의 상태벼롤 url을 지정해주고 return한다.
- 그 함수 자체를 getWeather에서 받아서 사용하면, rawValue의 값과 상관없이 사용할 수 있다.
 
```swift 
import UIKit

enum NetworkError: Error {
    case badURL
    case decodingError
}

enum TemperatureUnit: String {
    case imperial = "F"
    case metric = "C"
}

private func getWeatherURL(unit: TemperatureUnit) -> URL? {
    
    switch unit {
        case .imperial:
            return URL(string: "www.weather.com/?unit=fahrenheit")
        case .metric:
            return URL(string: "wwww.weather.com/?unit=celsius")
    }
    
}

func getWeather(unit: TemperatureUnit) throws {
    
    guard let weatherURL = getWeatherURL(unit: unit) else {
        throw NetworkError.badURL
    }
    
    print(weatherURL)
    
    // code to call the weather API
    
}

do {
    try getWeather(unit: .metric)
} catch {
    print(error)
}
```
