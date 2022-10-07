## filter 
- 변환타입이 Bool인 매개변수가 함수의 결과가 true이면 새로운 컨테이너에 값을 담아 반환한다.

```swift
// 이름이 4글자 이상인 사람만 추출하고 싶다.
var names = ["Alex", "John", "Steven", "Mary"]

names = names.filter { name in
    return name.count > 4
}

print(names)
 
struct Movie {
    let title: String
    let genre: String
}

var movies = [Movie(title: "Lord of the Rings", genre: "Fiction"), Movie(title: "ET", genre: "Fiction"),
              Movie(title: "Finding Nemo", genre: "Kids"), Movie(title: "Cars", genre: "Kids")]

// movie 구조체에서 gnere가 Kids인 영화제거!!
let kidMovies = movies.filter { movie in
    return movie.genre == "Kids"
}

print(kidMovies)

// 제목이 'Finding Nemo' 인 구조체 제거!!
let movieToRemove = Movie(title: "Finding Nemo", genre: "Kids")

movies = movies.filter { movie in
    return movie.title != movieToRemove.title
}

print(movies)
```
