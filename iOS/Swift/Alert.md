# Alert

## 예시코드 
## 확인 버튼
~~~
let alertController = UIAlertController(title: "제목", message: "적고싶은내용", preferredStyle: .alert)
let okAction = UIAlertAction(title: "확인", style: .default)
alertController.addAction(okAction)
            
self.present(alertController, animated: false)
~~~