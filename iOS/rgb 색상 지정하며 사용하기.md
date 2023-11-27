# rgb 색상 지정하며 사용하기

## 예시 코드
~~~
extension UIColor {
    static func rgb(red: CGFloat, green: CGFloat, blue: CGFloat) -> UIColor {
        return UIColor(red: red/255, green: green/255, blue: blue/255, alpha: 1)
    }
    static let twitterBlue = UIColor.rgb(red: 29, green: 161, blue: 242)
}
~~~