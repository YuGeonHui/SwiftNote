# Date

## DateType and Reference Date
> Reference date: 2001-01-01 00:00:00 / UTC

```swift
let now = Date()
print(now)

var dt = Date(timeIntervalSinceReferenceDate: 60 * 60) // Reference Data 이후로 1시간 뒤
print(dt)

dt = Date(timeIntervalSinceReferenceDate: -60 * 60) // Reference Data 이후로 1시간 이전
print(dt)
```

## TimeInterval 

```swift
let oneMillisecond = TimeInterval(0.001) 
let oneSec = TimeInterval(1)
let oneMin = TimeInterval(60)
let oneHour = TimeInterval(60 * 60)
let oneDay = TimeInterval(60 * 60 * 24)

Date(timeIntervalSinceNow: oneDay) // 24시간 후 날짜와 시간
Date(timeIntervalSince1970: oneDay) // API 통신은 해당 초기화를 사용한다.
```

## Calendar 

```swift 
Calendar.Identifier.gregorian // gregorian 달력으로 설정

Calendar.current // Iphone설정에서 선택되어 있는 달력 -> 최초 달력 유지
Calendar.autoupdatingCurrent // Iphone설정에서 선택되어 있는 달력 -> 달력 변경 시, 자동변경
```

## DateComponents

```swift
let now = Date()
let calendar = Calendar.current
let components = calendar.dateComponents([.year, .month, .day], from: now) // 원하는 값들을 선택해서 쓸 수 있다.

components.year // 현재 년도
components.month // 현재 달
components.day // 현재 날짜 

let year = calendar.component(.year, from: now) // 한 개만 받아오고 싶을 때

// 새로운 날짜 생성
var memorialDayComponents = DateComponents()

memorialDayComponents.year = 2014
memorialDayComponents.month = 4
memorialDayComponents.day = 16

let memorialDay = calendar.date(from: memorialDayComponents)
```

## Date Calculation

```swift 
extension Date {
    
    init?(year: Int, month: Int, day: Int, hour: Int = 0, minute: Int = 0, second: Int = 0, calendar: Calendar = .current) {
        
        var components = DateComponents()
        components.year = year
        components.month = month
        components.day = day
        components.hour = hour
        components.minute = minute
        components.day = day
        
        guard let date = calendar.date(from: components) else { return nil }
        
        self = date
    }
}

let calendar = Calendar.current
let worldCup2002 = Date(year: 2002, month: 5, day: 31)!

let now = Date()
let today = calendar.startOfDay(for: now) // (현재날짜) 0시 0분 0초로 나타내준다. 

// 100일 뒤 나타내기
var comps = DateComponents()
comps.hour = 12 // 시간 변동이 존재할 수 있다.
comps.day = 100

calendar.date(byAdding: comps, to: now)
calendar.date(byAdding: comps, to: today)

// 월드컵으로부터 며칠 지났는지
comps = calendar.dateComponents([.day], from: worldCup2002, to: today)
```
## TimeZone
```swift
let calendar = Calendar.current
var components = DateComponents()
components.year = 2014
components.month = 4
components.day = 16

components.timeZone = TimeZone(identifier: "Asia/Seoul")
calendar.date(from: components)

components.timeZone = TimeZone(identifier: "America/Los_Angeles")
calendar.date(from: components)

// iOS에서 사용하는 타임존 (약 400개)
for name in TimeZone.knownTimeZoneIdentifiers {
    print(name)
}
```









