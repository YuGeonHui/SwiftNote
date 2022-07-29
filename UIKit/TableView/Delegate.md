## UITableViewDelegate 
-  항목 관리, 섹션 헤더 및 바닥글 구성, 셀 삭제 및 순서 변경 등 수행 방법을 나타내준다.
-  필수로 구현해야 하는 함수는 없다.

## UITableViewDataSource
- 개체가 데이터를 관리하고 테이블 뷰에 셀을 제공하기 위해 사용하는 방법입니다.
- 데이터와 관련된 정보는 위의 프로토콜에서 정의힌다.
- 아래의 메소드를 필수로 구현해줘야 한다.

```swift 
// Return the number of rows for the table.     
override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
   return 0
}

// Provide a cell object for each row.
override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
   // Fetch a cell of the appropriate type.
   let cell = tableView.dequeueReusableCell(withIdentifier: "cellTypeIdentifier", for: indexPath)
   
   // Configure the cell’s contents.
   cell.textLabel!.text = "Cell text"
       
   return cell
}
```
