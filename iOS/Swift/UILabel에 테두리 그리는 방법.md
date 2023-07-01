# UILabel에 테두리 그리는 방법

<img width="532" alt="image" src="https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/d3a577d2-6240-4a01-b8d4-eac32d5fcdc8">  

## 예시 코드

~~~
import UIKit
class ViewController: UIViewController {

    @IBOutlet weak var label1: UILabel!
    @IBOutlet weak var label2: UILabel!
    @IBOutlet weak var label3: UILabel!
    @IBOutlet weak var label4: UILabel!
    @IBOutlet weak var label5: UILabel!
    @IBOutlet weak var label6: UILabel!

    override func viewDidLoad() {
        super.viewDidLoad()

        // label 1
        label1.layer.borderWidth = 1.0

        // label 2
        label2.layer.borderWidth = 5.0
        label2.layer.borderColor = UIColor.blue.cgColor

        // label 3
        label3.layer.borderWidth = 2.0
        label3.layer.cornerRadius = 8

        // label 4
        label4.backgroundColor = UIColor.cyan

        // label 5
        label5.backgroundColor = UIColor.red
        label5.layer.cornerRadius = 8
        label5.layer.masksToBounds = true

        // label 6
        label6.layer.borderWidth = 2.0
        label6.layer.cornerRadius = 8
        label6.backgroundColor = UIColor.yellow
        label6.layer.masksToBounds = true
    }
}
~~~  

# Reference
https://stackoverflow.com/questions/2311591/how-to-draw-border-around-a-uilabel/33015915#33015915  
