# Extension 

```swift
extension UIButton {
    
    func makeCircular() {
        
        self.clipsToBounds = true
        self.layer.cornerRadius = self.frame.size.width / 2
    }
}

extension Double {
    
    func round(to places: Int) -> Double {
        
        let precisionNumber = pow(10, Double(places))
        var n = self
        
        n = n * precisionNumber
        n.round()
        n = n / precisionNumber
        
        return n
    }
}

var myDouble = 3.14159
myDouble.round(to: 3) // 3.142
```
