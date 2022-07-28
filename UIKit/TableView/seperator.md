# Seperator
- section내부에 cell을 구분할 때 사용하는 선이다.

## seperatorStyle 
- sepeartor를 나타내는 스타일을 보여준다.

## seperatorColor
- seperator의 색을 정할 수 있다.

## seperatorInse
- seperator의 Inset을 적용할 수 있다.
- 위, 아래 방향은 무시된다. 
- 각각의 cell을 Deleate를 통하여, Inset을 적용할 수 있다. 

```swift 
class SeparatorViewController: UIViewController {
    
    let list = ["iMac Pro", "iMac 5K", "Macbook Pro", "iPad Pro", "iPhone X", "Mac mini", "Apple TV", "Apple Watch"]
    
    @IBOutlet weak var listTableView: UITableView!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        listTableView.separatorStyle = .singleLine
        listTableView.separatorColor = UIColor.systemBlue
        // top bottom은 무시된다.
        listTableView.separatorInset = UIEdgeInsets(top: 0, left: 0, bottom: 0, right: 0)
        // Inset을 설정하는 방법
        listTableView.separatorInsetReference = .fromCellEdges
    }
}


extension SeparatorViewController: UITableViewDataSource {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return 100
    }
    
    
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
        
        // inset은 각각 설정이 가능하다.
        if indexPath.row == 1 {
            cell.separatorInset = UIEdgeInsets(top: 0, left: 30, bottom: 0, right: 0)
        } else if indexPath.row == 2 {
            cell.separatorInset = UIEdgeInsets(top: 0, left: 0, bottom: 0, right: 30)
        } else {
            
            // cell을 재사용하기 때문에, 인셋을 초기값으로 돌려줘야 재사용된 cell에서 위의 Inset이 적용되지 않는다.
            cell.separatorInset = listTableView.separatorInset
        }
        
        cell.textLabel?.text = list[indexPath.row % list.count]
        return cell
    }
}
```
