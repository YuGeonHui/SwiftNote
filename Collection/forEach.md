## forEach

```swift
import UIKit

struct Movie {
    let title: String
    let genre: String
}

let movies = [Movie(title: "Lord of the Rings", genre: "Fiction"), Movie(title: "ET", genre: "Fiction"),
              Movie(title: "Finding Nemo", genre: "Kids"), Movie(title: "Cars", genre: "Kids")]


movies.forEach { movie in
    addToFavoriteList(movie)
}

func addToFavoriteList(_ movie: Movie) {
    
}

// index를 같이 출력하기 위해 enumerated()를 사용한다.
movies.enumerated().forEach { (index, movie) in
    print("Movie at \(index) has a title \(movie.title)")
}

```
