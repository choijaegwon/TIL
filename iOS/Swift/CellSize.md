# CellSize

## 예시코드 
### Cell 3*N 나열하기(양옆 마진값 x)
~~~
let cellSpacing:CGFloat = 4 // 셀의 간격
lazy var threePhoto:CGFloat = (UIScreen.main.bounds.width - self.cellSpacing * 2) / 3.0
    
private lazy var collectionView: UICollectionView = {
    let flowlayout = UICollectionViewFlowLayout()
    flowlayout.itemSize = CGSize(width: threePhoto, height: threePhoto)
    flowlayout.minimumInteritemSpacing = cellSpacing // 셀간의 간격
    flowlayout.minimumLineSpacing = cellSpacing // 가로줄 차이
    flowlayout.scrollDirection = .vertical
    let cv = UICollectionView(frame: .zero, collectionViewLayout: flowlayout)
    cv.showsVerticalScrollIndicator = false
    return cv
}()
~~~

### Cell 3*N 나열하기(양옆 마진값 o)
~~~
let cellSpacing:CGFloat = 4 // 셀의 간격
lazy var threePhoto:CGFloat = (UIScreen.main.bounds.width - self.cellSpacing * 4) / 3.0
    
private lazy var collectionView: UICollectionView = {
    let flowlayout = UICollectionViewFlowLayout()
    flowlayout.itemSize = CGSize(width: threePhoto, height: threePhoto)
    flowlayout.minimumInteritemSpacing = cellSpacing // 셀간의 간격
    flowlayout.minimumLineSpacing = cellSpacing // 가로줄 차이
    flowLayout.sectionInset = UIEdgeInsets.init(top: 0 , left: threePhoto, bottom: 0, right: threePhoto)
    flowlayout.scrollDirection = .vertical
    let cv = UICollectionView(frame: .zero, collectionViewLayout: flowlayout)
    cv.showsVerticalScrollIndicator = false
    return cv
}()
~~~