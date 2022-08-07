# Flow Layout 
- ```CollectionView```는 일반적으로 FlowLayout을 사용한다. 
- 자신이 원하는 뷰를 사용하고 싶은경우에는, Custom 하여 사용한다.

> layout Scroll 변경하는 방법
```swift
private func toggleScrollDirection() {

  guard let layout = listCollectionView.collectionViewLayout as? UICollectionViewFlowLayout else { return }
        
  listCollectionView.performBatchUpdates { // 애니메이션 추가
    layout.scrollDirection = layout.scrollDirection == .vertical ? .horizontal : .vertical
  }
}
```

# Flow Layout Delgate 
```swift
// MARK: - Flow Layout 관련 Delegate
extension FlowLayoutViewController: UICollectionViewDelegateFlowLayout {
    
    // 크기를 파악하기 위해서 (StoryBoard보다 우선순위가 높다.)
    func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, sizeForItemAt indexPath: IndexPath) -> CGSize {
        print("#1", #function)
        
        guard let layout = collectionViewLayout as? UICollectionViewFlowLayout else {
            return .zero
        }
        
        var bounds = collectionView.bounds // 컬렉션 뷰 크기를 변수로 설정
        debugPrint("bounds : \(bounds)")
        bounds.size.height += bounds.origin.y
        
        var width = bounds.width - (layout.sectionInset.left + layout.sectionInset.right)
        var height = bounds.height - (layout.sectionInset.top + layout.sectionInset.bottom)
        
        debugPrint("width : \(width)")
        debugPrint("height : \(height)")
        
        
        switch layout.scrollDirection {
            
        case .vertical:
            
            // 셀 높이를 5등분 한다. (lineSpacing을 빼고)
            height = (height - (layout.minimumLineSpacing * 4)) / 5
            
            if indexPath.item > 0 {
                width = (width - (layout.minimumInteritemSpacing * 2)) / 3
            }
            
        case .horizontal:
            
            width = (width - (layout.minimumLineSpacing * 2)) / 3
            
            if indexPath.item > 0 {
                height = (height - (layout.minimumInteritemSpacing * 4)) / 5
            }
        }
        
        return CGSize(width: width.rounded(.down), height: height.rounded(.down))
    }
    
//    func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, minimumInteritemSpacingForSectionAt section: Int) -> CGFloat {
//        print("#2", #function)
//        return 5
//    }
//
//    func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, minimumLineSpacingForSectionAt section: Int) -> CGFloat {
//        print("#3", #function)
//        return 5
//    }
//
//    func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, insetForSectionAt section: Int) -> UIEdgeInsets {
//        print("#4", #function)
//        return UIEdgeInsets(top: 5, left: 5, bottom: 5, right: 5)
//    }
}
```
