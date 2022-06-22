# Networking 

1. Create URL
2. Create a URLSession
3. Give URLSession a task 
4. Start the task 

# Intro

- 앞서 배운 HTTP 방식으로 네트워크 할수 있음
- iOS 네트워크 작업을 도와주는것이 `URLSession` 임

# URLSession

- `URLSession`을 이용해서 서버와 소통
    - `URLSessionConfiguration`
        - `.default`
            - 디스크를 이용한 정보 저장을 하는 configuration
            - 그냥 브라우저 띄울때
        - `.ephemeral`
            - default 랑 비슷한데, 몇가지 정보들을 저장하지 않음 (쿠키, 인증서 등)
            - 브라우저 시크릿 모드라고 생각하면 쉬움
        - `.background`
            - 네트워크를 통해 파일 다운로드 받을때,
            - 앱이 백그라운드에서 돌때도, 다운로드 시켜줄수 있음
    - `URLSession`
        - configuration 을 보고, 세션을 생성
    - `URLSessionTask`
        - dataTask
        - uploadTask
        - downloadTask
        
    
    ### URLSession  구조도
    ![image](https://user-images.githubusercontent.com/96224311/174943405-8a29c825-81e9-42d8-9498-a0e072361770.png)
    
    # Codable

- swift 객체를 외부 데이터 형태(주로 JSON)로 인코딩, 디코딩 가능하게 해주는 타입
- 네트워크 응답형태로 JSON이 거의 표준으로 사용
- Codable 을 이용하면,  JSON 과 swift 객체간 전환이 매우 쉬움

# URLSession + Combine

- `URLSessionDataTask` 에 대해서 publisher 제공
    - 따라서, 비동기 응답에 대한 작업이 더 수월함
